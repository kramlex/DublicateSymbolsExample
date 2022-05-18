# DublicateSymbolsExample

Connecting a static library (for example GMaps)  to an executable target and a dynamic framework that is also connected to an executable target and embedded in the application.

Podfile: 
```
target 'DublicateSymbolsExample' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!
  pod 'GoogleMaps', '6.2.1'

end

target 'GMapsExt' do
  use_frameworks! :linkage => :static
  pod 'GoogleMaps', '6.2.1'
end
```


After launching the application, you will see an error:
```
objc[36495]: Class GMSMapsClearcutClient is implemented in both /private/var/containers/Bundle/Application/484336E1-49FE-4D67-92DF-01BF8FFA71D8/DublicateSymbolsExample.app/Frameworks/GMapsExt.framework/GMapsExt (0x108038120) and /private/var/containers/Bundle/Application/484336E1-49FE-4D67-92DF-01BF8FFA71D8/DublicateSymbolsExample.app/DublicateSymbolsExample (0x105815660). One of the two will be used. Which one is undefined.
objc[36495]: Class GMSAPIClientParameters is implemented in both /private/var/containers/Bundle/Application/484336E1-49FE-4D67-92DF-01BF8FFA71D8/DublicateSymbolsExample.app/Frameworks/GMapsExt.framework/GMapsExt (0x108038170) and /private/var/containers/Bundle/Application/484336E1-49FE-4D67-92DF-01BF8FFA71D8/DublicateSymbolsExample.app/DublicateSymbolsExample (0x1058156b0). One of the two will be used. Which one is undefined.
...
```

Attention: This needs to be fixed or problems may appear during the execution of the program.
