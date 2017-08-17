# DynamicOoyalaWrapper

This repository wraps the static framework provided by Ooyala into a dynamic framework while exporting all the public headers provided by the wrapped static framework. It also adds a modulemap file to 
export the SDK as a module which is aboslutely necessary to import the sdk in swift framework targets. It also frees the 
clients from linking against almost 10 frameworks used by the Ooyala SDK. 
Finally the OoyalaSDK.framework provided by Ooyala has duplicate object files for a class, We have removed the duplicate 
object file in this binary so that we can use `-all_load`linker flag to load all binaries while linking statically
against that library. This means that the OoyalaSDK.framework present in this repo is a bit different from the one provided
by Ooyala.
Converting into a dynamic framework has the advantage that a framework and an application that uses that framework can both
link against this framework without having duplicate symbols since it is linked dynamically

Finally making this project let us a have a nice mechanisim for distribution such as carthage. 

# Installation

# Carthage
add `github "salmanjamil/DynamicOoyalaWrapper" == 1.0` in you cartfile and you are good to go.
