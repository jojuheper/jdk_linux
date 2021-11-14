# jdk_linux
Install JDK in Linux

--------------------

## Ubuntu

 *** Delete JDK ***

```bash

sudo dpkg --list | grep -i jdk
sudo apt-get purge jdk-* (jdk-* = jdk's name)

```

*** Install JDK ***

```bash

cd ~/Download/(folder where you have jdk)
tar xvzf jdk-*.tar.gz -C /tmp/
sudo su
if [ ! -d "/usr/lib/jvm" ]; then mkdir /usr/lib/jvm; fi
chown -R root:root /tmp/jdk-*
chmod -R +x /tmp/jdk-*/bin
mv /tmp/jdk-* /usr/lib/jvm

update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-*/bin/java 1065
update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-*/bin/javac 1065
update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/jdk-*/bin/javaws 1065 (sometime dont need it)
update-alternatives --config java

exit
ls /usr/lib/jvm
nano $HOME/.bashrc

(move last line)
export JAVA_HOME=/usr/lib/jvm/jdk-*    (remember javas name)
(save document)

bash
java -version

```

## Manjaro

```bash

pacman -sS java | grep jre
cd ~/Download/(folder where you have jdk)
tar xvzf jdk-*.tar.gz

sudo cp -r jdk-* /usr/lib/jvm    (remember jdk-* = jdks name)

sudo ln -s /usr/lib/jvm/jdk-*/bin/java /usr/bin/java
sudo ln -s /usr/lib/jvm/jdk-*/bin/javac /usr/bin/javac

nano ~/.bash_profile

(move last line)
export JAVA_HOME=/usr/lib/jvm/jdk-*
export PATH="$PATH:$JAVA_HOME/bin"
(save document)

java -version

```
