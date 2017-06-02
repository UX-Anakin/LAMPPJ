# Linux

## FAQ
1. Unable to lock the administration directory (var/lib/dpkg) is another process using it?
  - I get this error when trying to use **apt-get**:
  ```
  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
  E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
  ```
  **Answer**:
  I see pretty much all the answers recommend deleting the lock.I don't recommend doing that as a first measure.maybe if there is no alternative.The lock is placed when an apt process is running, and is removed when the process completes.If there is a lock with no apparent process running,this may mean the process got stuck for some reason.
  If you try:
  ```
  ps aux | grep apt
  ```
  that will catch processes containing the word **apt**, at least. if you see an **apt-get** process or an **aptitude** process that looks stuck, you can try:
  ```
  kill processnumber
  OR
  kill -9 processnumber
  ```
  This should kill the process and may remove the lock. Killing an **apt** or **aptitude** process is harmless unless it is actually in the middle of package installation.In any case, if the process got suck, you probably don't have a choice but to kill it.
  Kill a **dpkg** process directly, if present, is not a good idea, because if **dpkg** is active, it is probably manipulating the package database,and killing it may leave the package database in an inconsistent state.
  **This should be used as last resort.If you use this carelessly you can end up with a broken system.Please try the other answers before doing this**
  You can delete the lock file with the following command:
  ```
  sudo rm /var/lib/apt/lists/lock
  ```
  You may also need to delete the lock file in the cache directory
  ```
  sudo rm /var/cache/apt/archives/lock
  sudo rm /var/lib/dpkg/lock
  ```
  
