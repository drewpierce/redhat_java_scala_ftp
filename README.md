# redhat_java_scala_ftp
install recent versions of java / scala / ftp server on redhat
-------------------------------------------------

cd /op
sudo wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.rpm

-------------------------------------------------

sudo yum localinstall jdk-8u102-linux-x64.rpm
-- jdk is now installed in /usr/java/jdk1.8.0_102

-------------------------------------------------

-- delete the rpm:
rm ~/jdk-8u102-linux-x64.rpm

-------------------------------------------------

-- edit ~/.bash_profile to include:
# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs

export JAVA_HOME=/usr/java/jdk1.8.0_102/
export JRE_HOME=/usr/java/jdk1.8.0_102/jre

PATH=$PATH:$HOME/bin:$JAVA_HOME/bin

export PATH
-------------------------------------------------

-- set the active jdk version:
sudo alternatives --config java

-- check version:
java -version
java version "1.8.0_102"
Java(TM) SE Runtime Environment (build 1.8.0_102-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.102-b14, mixed mode)

-- end of Java section

x-x-x-x-x-x

if you want Scala, then:

wget http://www.scala-lang.org/files/archive/scala-2.11.8.tgz
tar xvf scala-2.11.8.tgz
sudo mv scala-2.11.8 /usr/lib
sudo ln -s /usr/lib/scala-2.11.8 /usr/lib/scala

-------------------------------------------------

-- edit ~/.bash_profile to include:
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs

export JAVA_HOME=/usr/java/jdk1.8.0_102/
export JRE_HOME=/usr/java/jdk1.8.0_102/jre

PATH=$PATH:$HOME/.local/bin:$HOME/bin:$JAVA_HOME/bin:/usr/lib/scala/bin

export PATH

-------------------------------------------------

-- check version:
scala -version
Scala code runner version 2.11.8 -- Copyright 2002-2016, LAMP/EPFL

-- end of Scala section

Online documentation poached for the above (some outdated):
[1]: https://www.mkyong.com/java/how-to-install-oracle-jdk-8-on-centos/
[2]: https://decisionstats.com/2014/04/15/installing-scala-on-centos/

