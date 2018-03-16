if [ $# != 1 ]; then
    echo User: ./CreateTag.sh comment
    exit
fi

SVN_ROOT_PATH="http://xxxx/xx_proj"
TAG_TARGET="xx_logic"

lastname=`svn ls ${SVN_ROOT_PATH}/tags | tail -1`
lastTag="${SVN_ROOT_PATH}/tags/$lastname"
echo lastTag:$lastTag >> TagLog.txt

var=`date +%Y%m%d_%H%M`
TAG_NAME="${TAG_TARGET}_${var}"

svn cp -m "$1" ${SVN_ROOT_PATH}/trunk  ${SVN_ROOT_PATH}/tags/${TAG_NAME}/
newTag="${SVN_ROOT_PATH}/tags/${TAG_NAME}/"
echo newTag:$newTag >> TagLog.txt

#svn info $lastTag
#svn info $newTag

rLast=`svn info $lastTag | awk  '/Rev:/{print $4}'`
rNew=`svn info $newTag   | awk  '/Rev:/{print $4}'`

echo "svn log -r$rLast:$rNew ${SVN_ROOT_PATH}/trunk | more" 

diffAttr=`svn log -r$rLast:$rNew ${SVN_ROOT_PATH}/trunk | more`

echo "$diffAttr" 
echo "$diffAttr" >>TagLog.txt
