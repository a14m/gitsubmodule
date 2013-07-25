gitsubmodule
------------
Complementary script to the `git submodule` providing easy update and remove.
* `git submodule update` : doesn't pull the latest submodule as I expect it to do.
* `git submodule remove` : isn't there and every time I try to do it, I have to google how.
 
Install
-
* download the scripts zip
* run `sudo ./gitsubmodule_install`

Uninstall
-
run `sudo ./gitsubmodule_install --uninstall`

Usage
-
`gitsubmodule [options | options[args]]`

###options

| option      |  desc. |
|-------------|--------|
| `-h,--help` |  displays the help|
| `--version` |  dispaays the version number|
| `-d,--dir =<args>`  |  provides the directory to the repo by default it's the current directory |
| `-u,--update,update` | issue update of the available submodules in the repo |
| `-r,--remove,remove` | prompt user to select one of the __available__ submodules to delete |
| `-r,--remove,remove =<args>`| prompt user to select one of the __matched__ submodules to delete |

See `gitsubmodule [remove|update] --help ` for specific help info

Update
-
Updates the available submodules found in the .gitmodules file

######Procedure :
1. cd into the submodule directory
2. stash the changes in the submodule
3. check out master branch to fix an issue where you are on (no-branch)
4. git pull latest changes
5. reapply stashed changes

Remove
-
* If no submodule was passed the script will find all the __available submodules__, and will prompt the user to choose one of them to delete.
* If submodule was provided the script will find all the __available matches__ to this submodule,

then it will prompt the user to choose one of the matches to delete it if more than 1 match occured, 

or will __automatically delete if only 1 match was found__.

######Procedure :
1. remove the submodule part from .gitmodules
2. remove the submodule part from .git/config
3. remove the the submodule cached directory
4. remove the submodule from .git/modules directory
5. commit the changes to the modified files only
6. remove the submodule directory

Examples
-
`gitsubmodule update -d ~/.vim` updates .vim submodules from outside `~/.vim`

`gitsubmodule update help` display help of the update

`gitsubmodule remove` prompt the user to remove one of the available submodules

`gitsubmodule -d ~/.vim -r nerd` show the matched submodules in the vim ex(nerdTree,nerdCommenter), if only one of them is available remove it and commit

COPYRIGHT
---------
Copyright (C) 2013, Ahmed Abdel Razzak. All rights reserved.

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the
Free Software Foundation; version 2 of the License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, write to the Free Software Foundation, Inc., 59
Temple Place, Suite 330, Boston, MA 02111-1307 USA or see http://www.gnu.org/licenses/.
