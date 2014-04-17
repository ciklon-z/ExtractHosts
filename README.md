ExtractHosts
============
Extracts hosts (IP/Hostnames) from files.  Hosts can be extracted from text files, PE, etc.  Any file that keeps the
host in plaintext without obscuring it, this should extract it.

The name came about when polling random people on the street about the idea, and they responded, "eh?".  With this installed,
all you need to type is 'eh' to start pulling hosts from input.

Installation
============
    git clone https://github.com/bwall/ExtractHosts.git
    cd ExtractHosts
    sudo python setup.py install
Examples
========
The following are just some example usages
help
----
    bwall@research:~$ eh -h
    usage: /usr/local/bin/eh [-h] [-v] [-r] [-f] [-d] [-T] [path [path ...]]

    Identifies and extracts domains and IPs from files

    positional arguments:
      path                  Paths to files or directories to scan (if not
                            supplied, stdin is the file being read)

    optional arguments:
      -h, --help            show this help message and exit
      -v, --version         show program's version number and exit
      -r, --recursive       Scan paths recursively
      -f, --show-files      Show file names along with results
      -d, --hide-duplicates
                            Hide duplicate results (hides per file when show-files
                            is enabled)
      -T, --test            Run some quick self tests

    /usr/local/bin/eh v1.0.0 by Brian Wallace (@botnet_hunter)
wget
----
    bwall@research:~$ wget http://bwall.github.io/ -qO- | eh -d
    bwall.github.io
    twitter.com
    gmail.com
    github.com
    README.md
    ajax.googleapis.com
    crypto-js.googlecode.com
    google-analytics.com
malware
-------
The 0686429b86844d9d1a14a159a0263b9bfcea4fd247c77537aa0278c9c5cb4ac3 file is a sample of the POS malware, Dexter, created for demo purposes.

    bwall@research:~$ eh 0686429b86844d9d1a14a159a0263b9bfcea4fd247c77537aa0278c9c5cb4ac3
    houseofcarders.com

File system recursion
---------------------
    bwall@research:~$ eh -drf Downloads/PEStudio/
    /home/bwall/Downloads/PEStudio/PeStudioFunctionsDeprecated.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioFunctionsDeprecated.xml	msdn.microsoft.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListFunctions.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioEvasions.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioIndicators.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/ChangeLog.txt	winitor.com
    /home/bwall/Downloads/PEStudio/ChangeLog.txt	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioThresholds.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioWhiteListSections.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListLibraries.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioOrdinals.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioVirusTotal.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioCodePages.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioCodePages.xml	msdn.microsoft.com
    /home/bwall/Downloads/PEStudio/PeStudioWhiteListLibraries.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioFeatures.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudio.exe	6.0.0.0
    /home/bwall/Downloads/PEStudio/PeStudioSettings.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	internetmailru.cdnmail.ru
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	sputnik.mail.ru
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	mail.ru
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	Command.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	127.0.0.1
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	2.0.0.1
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	www.memtest86.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	boxedapp.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	PAYPAL.COM
    /home/bwall/Downloads/PEStudio/PeStudioBlackListStrings.xml	start.spoon.net
    /home/bwall/Downloads/PEStudio/PeStudioFunctionsUndocumented.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioWellKnownResources.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioFunctionsMapping.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeParser.dll	776::06
    /home/bwall/Downloads/PEStudio/PeParser.dll	::
    /home/bwall/Downloads/PEStudio/PeParser.dll	3::
    /home/bwall/Downloads/PEStudio/PeStudioTranslations.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListLanguages.xml	www.winitor.com
    /home/bwall/Downloads/PEStudio/PeStudioBlackListLanguages.xml	msdn.microsoft.com

TODO
====
* IPv6 regex needs to be shorted and heavily tested
* Heavier testing
* Improve performance
* Buffer reading the file into RAM instead of all at once
* Multiple core processing support