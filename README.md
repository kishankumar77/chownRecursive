Description:
    This script will change the files/dirs ownership within a directory

Syntax:
    chowndir.pl --dirpath="/u/testdir/mydir" --touser="user2" --excludedir="testdir1"


Following Changes needs to be make after the tar ball is extracted to the local directory:

chowndir.pl script -  is dependent on BBSur.pm and BBInit.pm, so library path to be changed to your local lib path where you extract the tar ball chownExt.Cust.tar to be changed below lib path:
use lib '/u/rtpbuild/jeyaprak/testing/chownExt/lib';


BBSur.pm -  is dependent on  BBInit.pm, so library path to be changed to your local lib path where you extract the tar ball chownExt.Cust.tar to be changed below lib path:
use lib '/u/rtpbuild/jeyaprak/testing/chownExt/lib';
 
 BBInit.pm -
 the following tools path needs to be changed to your local paths 

 our $BB_CMD_SUR = '/u/rtpbuild/kishank/chownExt/sur';
 our $BB_LOGFILE = 'logfile';
 our $BB_PFIND = '/u/rtpbuild/kishank/chownExt/pfind';
 our $BB_FILELIST                   = ".filelist";
 our $BB_CMD_CAT                    = "/bin/cat";
 our $BB_CMD_TR                     = "/usr/bin/tr";
 our $BB_CMD_XARGS                  = "/usr/software/bin/xargs";
 our $BB_CMD_CUSTOM_CHOWN           = "/u/rtpbuild/kishank/chownExt/simple_chown";

 sur_dispatch -  is dependent on  BBInit.pm, so library path to be changed to your local lib path where you extract the tar ball chownExt.Cust.tar to be changed below lib path:
 use lib '/u/rtpbuild/jeyaprak/testing/chownExt/lib';

 sur.c
 sur.c:strcat (surcmd, "/u/dummyuser/chownExt/sur_dispatch");
 change it to sur_dispatch local path
 Run the below command
 $ make all

 Binary customization:
 if you make any changes to sur  & simple_chown binary - need to modify the sur.c & simple_chown.c source files and rebuild it ( make all )

 to make changes to pfind binary - you need to make changes in pfind_src/pfind.c and rebuilt  by changing the local paths in Makefile 


NOTE:
The Code is tested on RHEL 6.4 ( Santiago ) machines containing 40 cores.
On 87GB directory size containing 932321 files/dirs, the script took avg 50sec to complete
