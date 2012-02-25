# CM9 for Kindle Fire

## Info

|||
|-----------------------------------:|:--------------------------|
|**Discussion thread**: | http://forum.xda-developers.com/showthread.php?t=1411895
|**Building thread**:   | http://forum.xda-developers.com/showthread.php?p=20844007#post20844007
|**IRC Channel**:   	| #kindlefire-dev on freenode
|**Bug List**:	    	| https://docs.google.com/spreadsheet/ccc?key=0ArJmKQhhE5AFdGd2U0F3dFlkcno3dmdreFRtWUUtYVE#gid=0


## Building 

### Initialize
[setup linux/OS X](http://source.android.com/source/initializing.html) please note: it must be sun-java-6, not openjdk

### Download CM9 sources

```bash
mkdir cm9
cd cm9/
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > repo
chmod a+x repo
./repo init -u git://github.com/CyanogenMod/android.git -b ics
./repo sync -j16
```

### Compile

```bash
source build/envsetup.sh
brunch otter -j$(grep -c processor /proc/cpuinfo)
```

### Clean up repo

If you messed up your repo, clean it up (it will reset things like SystemUI, but not the device/vendor tree):

```bash
make clean
./repo forall -c "git reset --hard HEAD"
./repo forall -c "git clean -fdx"
./repo sync -j16
```