一个基于innosetup的 nodejs自动化打包工具，通过json配置，可灵活定制安装界面和安装流程，为nwjs、electron或者其他应用进行exe的打包。

# screenshot
![screenshot](https://raw.githubusercontent.com/1inus/node-inno/master/screenshot.png)

# npm

[npm](https://www.npmjs.com/package/node-inno)

```shell
npm install node-inno
```

# how to use

## create build directory

Create the build directory in the root directory.

``` js
|-xxx
|-build
  |-inno-resource //non-essential. pictures of the installation package
  | |-bg.png
  | |-...
  |
  |-build.json

```

## config build.json

```json
{
	"installDetail": {
		"createShortcut": true,
		"startupOnFinish": true,
		"startupOnBootstrap": true,
		"agreeLicense": true,
		"installPath": "",
		"checkUninstallBeforeInstall":true,
		"requireUninstallBeforeInstall":false,
		"defaultInstallDir": "C:\\Program Files (x86)\\node-inno",
		"installerOutputDir": "C:/Users/cnlia/Desktop"
	},
	"app": {
		"id": "TakeColor 1.0.0",
		"name": "TakeColor",
		"version": "",
		"publisher": "maker",
		"mainPage": "",
		"comments": "myapp_installer",
		"exe": "build/app/TakeColor.exe",
		"package": "build/app/*"
	},
	"registry": [{
		"root": "HKCR",
		"subkey": "test\\DefaultIcon",
		"type": "string",
		"name": "URL Qiaoker Protocol",
		"value": "{app}\\test.exe",
		"flags": "CreateValueIfDoesntExist"
	}],
	"ui": {
		"encoding": "gbk",
		"fontName": "Microsoft YaHei",
		"clientWidth": 800,
		"clientHeight": 500,
		"checkboxSize":16,
		"uninstallMsgbox": {
			"text": "检测到已经安装xxxxx，安装前是否卸载HTML DOM confirm()",
			"color":"000000",
			"fontSize":16,
			"width":520,
			"height":430,

			"textTop":249,
			"textLeft":65,
			"textWidth":400,
			"textHeight":60,

			"btnOkTop":318,
			"btnOkLeft":275,
			"btnOkWidth":160,
			"btnOkHeight":60,

			"btnCancelTop":318,
			"btnCancelLeft":85,
			"btnCancelWidth":160,
			"btnCancelHeight":60
		},
		"checkTaskMsgbox": {
			"text": "检测到xxx正在运行，是否结束任务",
			"color":"000000",
			"fontSize":16,
			"width":520,
			"height":430,

			"textTop":249,
			"textLeft":65,
			"textWidth":400,
			"textHeight":60,

			"btnOkTop":318,
			"btnOkLeft":275,
			"btnOkWidth":160,
			"btnOkHeight":60,

			"btnCancelTop":318,
			"btnCancelLeft":85,
			"btnCancelWidth":160,
			"btnCancelHeight":60
		},
		"htmlAdBar": {
			"top": 0,
			"left": 0,
			"width": 800,
			"height": 350,
			"show": false
		},
		"simpleAdBar": {
			"images": [],
			"interval": 5000,
			"top": 0,
			"left": 0,
			"width": 800,
			"height": 350,
			"timeInterval": 3000,
			"show": true
		},
		"licenseText": {
			"text": "许可协议",
			"top": 482,
			"left": 172,
			"color": "FF8833",
			"show": true
		},
		"moreOptions": {
			"text": "更多安装选项",
			"top": 12,
			"left": 12,
			"show": true,
			"color": "000000"
		},
		"licenseCheckbox": {
			"text": "已经阅读",
			"top": 478,
			"left": 91,
			"checked": true,
			"show": true,
			"color": "000000"
		},
		"createShortcutCheckbox": {
			"text": "创建桌面快捷方式",
			"top": 478,
			"left": 465,
			"checked": true,
			"show": true,
			"color": "000000"
		},
		"startupOnFinishCheckbox": {
			"text": "立即运行程序",
			"top": 478,
			"left": 352,
			"checked": true,
			"show": true,
			"color": "000000"
		},
		"startupOnBootstrapCheckbox": {
			"text": "开机启动",
			"top": 478,
			"left": 253,
			"checked": true,
			"show": true,
			"color": "000000"
		},
		"installDirInput": {
			"top": 429,
			"left": 154,
			"height": 35,
			"width": 400,
			"color": "000000",
			"show": true,
			"fontSize":14,
			"enabled":false
		},
		"installDirBrowserButton": {
			"top": 429,
			"left": 553,
			"height": 35,
			"width": 80,
			"show": true
		},
		"cancleInstallMsgbox": {
			"text": "确定取消安装吗？",
			"show": true
		},
		"progressBar": {
			"top": 435,
			"left": 50,
			"width": 700,
			"height": 20,
			"show": true
		},
		"progressText": {
			"top": 390,
			"left": 0,
			"width": 800,
			"height": 30,
			"color": "E78E0E",
			"show": true
		},
		"installButton": {
			"top": 365,
			"left": 274,
			"width": 230,
			"height": 50,
			"show": true
		},
		"finishText": {
			"text": "安装完毕",
			"top": 385,
			"left": 0,
			"width": 800,
			"height": 30,
			"color": "20ad11",
			"show": true
		},
		"finishButton": {
			"top": 428,
			"left": 275,
			"width": 250,
			"height": 50,
			"show": true
		},
		"minimizeButton": {
			"top": 4,
			"left": 755,
			"width": 16,
			"height": 16,
			"show": true
		},
		"closeButton": {
			"top": 4,
			"left": 779,
			"width": 16,
			"height": 16,
			"show": true
		}
	}
}
```

## build

```javascript
let { NodeInno } = require("node-inno");
NodeInno.build(config, (code)=>{
	
});
```

For more details, please refer to the demo under the source directory.