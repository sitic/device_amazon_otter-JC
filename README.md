# CM9 for Kindle Fire

## Info

|||
|-----------------------------------:|:--------------------------|
|**Discussion thread**: | http://forum.xda-developers.com/showthread.php?t=1411895
|**Building thread**:   | http://forum.xda-developers.com/showthread.php?p=20844007#post20844007
|**IRC Channel**:   	| #kindlefire-dev on freenode
|**Bug List**:	    	| https://docs.google.com/spreadsheet/ccc?key=0AqxTqi6CPt-RdEtHbFhHNDdjZGVONld1OGFEYmRiWUE#gid=0


## Building 

### Initialize
[setup linux/OS X](http://source.android.com/source/initializing.html) please note: it must be sun-java-6, not openjdk

### Download sources

```bash
mkdir cm9
cd cm9/
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/repo
chmod a+x ~/repo
repo init -u git://github.com/CyanogenMod/android.git -b ics
wget -O .repo/local_manifest.xml https://raw.github.com/sitic/android_local_manifest/master/local_manifest.xml 
repo sync -j16
./vendor/cm/get-prebuilts
```

### Compile

```bash
source build/envsetup.sh
brunch otter -j$(grep -c processor /proc/cpuinfo)
```