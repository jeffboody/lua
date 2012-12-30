Readme
======

This is Lua 5.2.1, released on 08 Jun 2012.

For installation instructions, license details, and
further information about Lua, see doc/readme.html.

Android
=======

This git repository contains a patch to build the Lua library with the
Android NDK. To use this submodule in an Android project follow these
steps.

1. clone the Lua repository under the project/jni directory
2. add "lua" to the APP_MODULES in project/jni/Application.mk
3. include the Lua Android.mk from your main Android.mk
4. add "-llua" to your main Android.mk
5. add "System.loadLibrary("lua");" to the static section of your Java class.

Send questions or comments to Jeff Boody - jeffboody@gmail.com

Example Android.mk
------------------

	LOCAL_PATH := $(call my-dir)
	
	# include libraries in correct order
	include $(LOCAL_PATH)/lua/Android.mk
	
	include $(CLEAR_VARS)
	LOCAL_MODULE    := MyProgram
	LOCAL_CFLAGS    := -Wall
	LOCAL_SRC_FILES := main.c
	LOCAL_LDLIBS    := -Llibs/armeabi -llog -llua
	
	include $(BUILD_SHARED_LIBRARY)
