About
===

The semi-official tutorial on how to create externs on both hxcpp/hl in haxe!

HXCPP
===

Just:
```haxe
@:buildXml('<include name="../../../build.xml" />')
@:unreflective @:keep
@:include("path here")
extern class EXTERN {
	@:native("destroy") static function destroy():Void;
	@:native("start") static function start():Void;
	@:native("stop") static function stop():Void;
	@:native("stopped") static function stopped():Int;
    // ...
}
```

Your build.xml should be stored on the same path as the Project.xml and should be like this:
```xml
<xml>
	<pragma once="true" />
	<set name="PROJECT_DIR" value="${this_dir}/Source" />

	<files id="haxe">
		<compilerflag value="-I${PROJECT_DIR}/[extern]" />
	</files>

	<files id="extern">
		<compilerflag value="-I${PROJECT_DIR}/[extern]" />
		<compilerflag value="-I${PROJECT_DIR}/[extern]/include" />
        <!-- You should add whatever include files are inthere-->
		<!--<compilerflag value="-I${PROJECT_DIR}/miniaudio/signalsmith-stretch" />-->
        <!-- Please do this -->
		<file name="${PROJECT_DIR}/[extern]/[cpp_extern].cpp" />
	</files>

	<target id="haxe">
		<files id="extern" />
	</target>
</xml>
```

And that's it! You can now compile your extern!

Hashlink
===

https://github.com/HaxeFoundation/hashlink/wiki

https://github.com/josuigoa/hl-extension

Man read it

Note
===

This was written 13:35 after midnight.