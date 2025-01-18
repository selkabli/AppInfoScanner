![License](https://img.shields.io/badge/Version-V1.0.8-red) ![Language](https://img.shields.io/badge/Language-Python3-blue) ![License](https://img.shields.io/badge/License-GPL3.0-orange) [![HitCount](https://hits.dwyl.com/kelvinBen/kelvinBen/AppInfoScanner.svg?style=flat&show=unique)](http://hits.dwyl.com/kelvinBen/kelvinBen/AppInfoScanner)

This project is currently just the tip of the iceberg in the planned project. If you are interested in this project or want to participate in the development or translation work of future projects, please send an email to blsm@vip.qq.com to explain your capabilities and requests.

## AppInfoScanner

A tool for information collection scanning, suitable for scenarios such as HW operations/red teams/penetration testing teams, which helps penetration testers, attack team members, and red team members quickly collect key asset information from mobile apps (Android, iOS), web apps, H5, and static websites. It provides basic output information such as: Title, Domain, CDN, Fingerprint, Status information, etc.

## Introduction
- The current developer of this project is an individual developer who also has a job. New features or demands will be developed in leisure time, and bugs will be handled as a priority.
- If you encounter any issues during use or have new demands, please submit bug feedback at [Issues](https://github.com/kelvinBen/AppInfoScanner/issues). Please read the "Frequently Asked Questions" section before submitting a bug.
- If you find this project useful, please click the "star" button in the upper-right corner of the project.
- If you want to follow up on new versions, please click the "Watch" button in the upper-right corner.
- If you want to contribute to this project, please click the "Fork" button in the upper-right corner. Otherwise, do not click the "Fork" button.

## Disclaimer
Do not use the technologies or code from this project for **illegal purposes** such as creating malicious software, stealing software copyrights/intellectual property, or improper profit-making. Engaging in such activities or using this project to sniff data from programs that are not owned by you may violate the laws of the People's Republic of China, including Articles 217 and 286 of the Criminal Law, the Cybersecurity Law, and the Computer Software Protection Regulations. The technologies mentioned in this project should only be used in legitimate scenarios, such as private learning and testing. Any criminal or civil liabilities resulting from the misuse of this technology are not the responsibility of the project author.

## Applicable Scenarios
- Key asset information collection in penetration testing of mobile apps, such as collecting URL addresses, IP addresses, keywords, etc.
- Key asset information collection in large-scale red team/defense drills for mobile apps, such as collecting URL addresses, IP addresses, keywords, etc.
- Collection of URL addresses, IP addresses, keywords, etc., from the source code of web websites (can be from open-source code or right-click "Save As" on the webpage source code).
- Collection of URL addresses, IP addresses, keywords, etc., from H5 pages.
- Collection of basic information for a specific app.

## Features:
- [x] Supports directory-level bulk scanning
- [x] Supports information collection for DEX, APK, IPA, MACH-O, HTML, JS, Smali, ELF, and other files
- [x] Supports automatic downloading of APK, IPA, H5 files and one-click information collection
- [x] Supports custom request headers, request messages, and request methods
- [x] Supports custom rules, allowing flexible scanning rules
- [x] Supports custom ignoring of resource files
- [x] Supports custom Android shell rule configuration
- [x] Supports custom middleware rule configuration
- [x] Supports detection of Android reinforcement shell and official IPA shell
- [x] Supports IP addresses, URL addresses, and middleware (json and xml components) information collection
- [x] Supports collection of content under Android package names
- [x] Supports network sniffing functionality and provides basic output information
- [x] Supports Windows, MacOS, and *nix series operating systems
- [x] Simple AI recognition function for fast filtering of third-party URLs
- [ ] Fingerprint recognition module
- [ ] Add internationalization language packs
- [ ] One-click automatic fixing of APK files
- [ ] Automatic unboxing when a shell is detected

## Screenshots

![](result.png)

## Environment Requirements
- Apk file analysis requires Java environment, Java version 1.8 and below
- Python3 runtime environment

## Directory Structure

```
AppInfoScanner
|-- libs The core code of the program
|-- core
|-- __init__.py Global configuration information
|-- parses.py Used to parse static information in the file
|-- download.py Used to automatically download APP or H5 pages
|-- net.py Used to sniff the network and obtain basic information
|-- task
|-- __init__.py Directory initialization file
|-- base_task.py Unified task scheduling center
|-- android_task.py Used to handle Android-related tasks
|-- download_task.py Used to handle tasks for automatically downloading APP or H5
​ |-- ios_task.py Used to handle iOS-related tasks
|-- net_task.py Used to handle network sniffing related tasks
​ |-- web_task.py Used to handle Web-related tasks, such as right-click source code of web pages, static information related to H5
​ |-- tools Tools that the program needs to rely on
​ |-- apktool.jar Used to decompile apk files. Different platforms may need to switch themselves. ​ |-- baksmali.jar Used to decompile dex files. Different platforms may need to switch themselves. ​ |-- strings.exe Used to obtain iPA string information under windows 32 ​ |-- strings64.exe Used to obtain iPA string information under windows 64 ​ |-- __init__.py Directory initialization file ​ |-- app.py Main running program ​ |-- config.py Configuration file for the entire program ​ |-- README.md Program instructions ​ |-- requirements.txt Dependent libraries to be installed in the program ​ |-- update.md Program historical version information ​``` ​## Instructions ​ ​1. Download ​``` ​ git clone https://github.com/kelvinBen/AppInfoScanner.git ​ Or copy the following link to the browser to download the latest official version ​ https://github.com/kelvinBen/AppInfoScanner/releases/latest ​Domestic fast download channel:

git clone https://gitee.com/kelvin_ben/AppInfoScanner.git

```

2. Install dependent libraries
```
cd AppInfoScanner
python -m pip install -r requirements.txt
```

3. Run (Basic version)

- Scan Android application APK files, DEX files, APK file download addresses to be downloaded, and directories to save files to be scanned

```
python app.py android -i <Your APK File or DEX File or APK Download Url or Save File Dir>
```

- Scan iOS application IPA files, Mach-o files, IPA file download addresses to be downloaded, and save files to be scanned

```
python app.py ios -i <Your IPA file or Mach-o File or IPA Download Url or Save File Dir>
```

- Scan Web site files, directories, and site URls to be cached

```
python app.py web -i <Your Web file or Save Web Dir or Web Cache Url>
```

## Advanced Operation Guide

### Basic Command Format
```
python app.py [TYPE] [OPTIONS] <The URL or directory to scan>
```

### Symbol Information Description

```
<> represents the file or directory or URL address to be scanned
| or relationship, only one can be selected
[] represents the parameter to be input
```

### TYPE parameter detailed description
This parameter type corresponds to [TYPE] in the basic command format. Currently, only three types of [android/ios/web] are supported, and one of the three types must be specified.

```
android: used to scan the contents of files related to Android applications
ios: used to scan the contents of files related to iOS applications
web: used to scan the contents of files related to WEB sites or H5
```

Supports automatic correction based on the suffix name. Even if the input is ios, the file name of the parameter input by -i is XXX.apk, then the android-related scan will be performed.

### OPTIONS parameter detailed description
This parameter type corresponds to [OPTIONS] in the basic command format, and supports multiple parameters to be used together

```
-i or --inputs: Enter the file, directory or URL address of the file to be scanned, if the path is too long, please add " to wrap it, this parameter is required.
-r or --rules: Enter the temporary scanning rules for the file content to be scanned.
-s or --sniffer: Enable the network sniffing function, which is enabled by default.
-n or --no-resource: Ignore all resource files, including resource files in the network sniffing function (sniffer_filter related rules need to be configured in config.py first), and the default is not to ignore resources.
-a or --all: Output all result sets that meet the scanning rules, which is enabled by default.
-t or --threads: Set the number of concurrent threads, which defaults to 10 concurrent threads.
-o or --output: Specify the output directory for the scan results and temporary files generated during the scan, which defaults to the directory where the script is located.
-p or -- package: Specify the JAVA package name information of the Android APK file or DEX file to be scanned. This parameter can only be used in the android type.
```

### Specific usage method

#### Basic operations related to Android
- Scan local APK files
```
python app.py android -i <Your apk file>

Example:

python app.py android -i C:\Users\Administrator\Desktop\Demo.apk
```

- Scan local Dex files
```
python app.py android -i <Your DEX file>

Example:

python app.py android -i C:\Users\Administrator\Desktop\Demo.dex

```
- Scan the APK file contained in the URL address
```
python app.py android -i <APK Download Url>

Example:

python app.py android -i "https://127.0.0.1/Demo.apk"

```
Note that if the URL address is too long, it needs to be wrapped in double quotes (")

#### Basic operations related to iOS
- Scan local IPA files
```
python app.py ios -i <Your ipa file>

Example:

python app.py ios -i "C:\Users\Administrator\Desktop\Demo.ipa"
```

- Scan local Macho files
```
python app.py ios -i <Your Mach-o file>

Example:

python app.py ios -i "C:\Users\Administrator\Desktop\Demo\Payload\Demo.app\Demo"
```

- Scan the IPA file contained in the URL address
```
python app.py ios -i <IPA Download Url>

Example:

python app.py ios -i "https://127.0.0.1/Demo.ipa"

```
Note that if the URL address is too long, it needs to be wrapped in double quotes ("), and scanning of IPA files in the Apple Store is not supported for the time being

#### Basic Web-related operations

- Scan local WEB sites

```
python app.py web -i <Your web file>

Example:

python app.py web -i "C:\Users\Administrator\Desktop\Demo.html"

```
- Scan the WEB site file contained in the URL address
```
python app.py web -i <Web Download Url>

Example:

python app.py web -i "https://127.0.0.1/Demo.html"

```

#### Common operations

The following operations are all based on the Android type as an example:

- Scan a local directory
```
python app.py android -i <Your Dir>

Example:

python app.py android -i C:\Users\Administrator\Desktop\Demo
```

- Add temporary rules or keywords

```
python app.py android -i <Your apk> -r <the keyword | the rules>

Example:
Add a scan for Baidu domain name

python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -r ".*baidu.com.*"
```

- Turn off network sniffing
```
python app.py android -i <Your apk> -s

Example:
python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -s

```
- Ignore all resource files
```
python app.py android -i <Your apk> -n

Example:
python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -n

```

- Disable the function of outputting all contents that meet the scanning rules
```
python app.py android -i <Your apk> -a

Example:

python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -a
```

- Set the number of concurrent threads
```
python app.py android -i <Your apk> -t 20

Example:
Set 20 concurrent threads
python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -t 20
```
- Specify the output directory of the result set and cache file
```
python app.py android -i <Your apk> -o <output path>

Example:
For example, output to the Temp directory on the desktop
python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -o C:\Users\Administrator\Desktop\Temp
```

- For the file contents under the specified package name

```
python app.py android -i <Your apk> -p <Java package name>
Example:
For example, you need to filter the content under the package name com.baidu

python app.py android -i C:\Users\Administrator\Desktop\Demo.apk -p "com.baidu"

```

## Advanced version instructions
The program in this project is only a basic framework, and some basic rules will be built in. Not every input content can complete the relevant scanning work. Therefore, you can configure the relevant rules according to your needs. Excellent configuration content can achieve qualitative results.

- The configuration file path is the config.py file in the root directory, which is the same level directory as README.md

### Configuration item description
```
filter_components: This configuration item is used to configure the content of related components, including Json components or XML components, etc.
filter_strs: Used to configure the content of the file to be scanned. For example, if you need to scan the port number, the configuration is: "r'.*://([\d{1,3}\.]{3}\d{1,3}).*'"
filter_no: Used to ignore unwanted content in the scanned file
shell_list: Used to configure Android-related shell features
web_file_suffix: Configure the suffix name of the WEB file to be scanned here
sniffer_filter: Used to configure the suffix name of the file that needs to be ignored for network sniffing
headers: Used to configure the request header information required during the automatic download process
data: Used to configure the request message body required during the automatic download process
method: Used to configure the request method required during the automatic download process
```

## FAQ

### 1. Too much junk data in information retrieval?

```
Method 1: Adjust the rule information in config.py according to the actual situation
Method 2: Ignore resource files
```

### 2. Error: Error: This application has shell, the retrieval results may not be accurate, Please remove the shell and try again!

This means that the application to be scanned has a shell, and it needs to be unshelled/smashed before scanning. Currently, the following tools can be used for unshelling/smashing
```

Android:
xposed module: dexdump
frida module: FRIDA-DEXDump
Rootless unshelling: blackdex
iOS:
firda module:
Windows system use: frida-ipa-dump
MacOS system use: frida-ios-dump
```

### 3. Error: File download failed! Please download the file manually and try again.

File download failed.
```
1) Please check if the URL you entered is correct
2) Please check if there is a problem with the network or configure the request header information (headers), request message body (data), and request method (method) in the configuration file config.py and save and execute again.
```
### 4. Error: Decompilation failed, please submit error information at https://github.com/kelvinBen/AppInfoScanner/issues"

File decompilation failed.

```
Please submit the error screenshot and the corresponding APK file to https://github.com/kelvinBen/AppInfoScanner/issues. The author will handle it in time after seeing it.
```
## Custom rule addition

Custom rule submission path:

[Click to add custom rules](https://github.com/kelvinBen/AppInfoScanner/issues/7）

Submission format:
```
1. Add APP custom components

For example: The rules of fastjson are as follows:
APP component: fastjson com.alibaba.fastjson

2. The string to be searched

For example: The rules for querying Alibaba's AK are as follows:
String:
Alibaba Cloud AK .*accessKeyId.*".*"

3. Web file suffixes to be searched

For example: the rules for jsp files are as follows:
Website: java language jsp

4. Android shell rules
For example: the shell rules for a certain digital company are as follows:
Shell: a certain digital company com.stub.StubApp

```

## Contact the author

**WeChat**: bromomo (please note: GitHub when adding friends)

**WeChat group**:

![image](https://user-images.githubusercontent.com/19259171/177041407-66b627d7-39b5-40e7-9858-85dca5b4f958.png)

If you cannot join, please add WeChat friends and join the group.

**Email**: blsm@vip.qq.com

You can add the author as a friend for submitting requirements, submitting BUG fixes, technical exchanges, and business cooperation.

## Stargazers over time
[![Stargazers over time](https://starchart.cc/kelvinBen/AppInfoScanner.svg)](https://starchart.cc/kelvinBen/AppInfoScanner)

## 404StarLink 2.0 - Galaxy
![](https://github.com/knownsec/404StarLink-Project/raw/master/logo.png)

AppInfoScanner is a part of 404Team [StarLink Project 2.0](https://github.com/knownsec/404StarLink2.0-Galaxy). If you have any questions about AppInfoScanner or want to find friends to communicate, you can refer to the StarLink Project group joining method.

[https://github.com/knownsec/404StarLink2.0-Galaxy#community](https://github.com/knownsec/404StarLink2.0-Galaxy#community)
