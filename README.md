# Repro of Protobuf gradle plugin warning

## Steps:

1. `./gradlew extractIncludeDebugAndroidTestProto`

## Expected

No warnings since app/build.gradle is only setting
```groovy
android {
    sourceSets {
        main {
            proto.srcDir 'proto'
        }
    }
}
```

## Actual

```text
> Task :app:extractIncludeDebugAndroidTestProto
proto file '/ssd/ssd1/temp/ProtoProject/app/proto/icing/proto/status.proto' directly specified in configuration. It's likely you specified files('path/to/foo.proto') or fileTree('path/to/directory') in protobuf or compile configuration. This makes you vulnerable to https://github.com/google/protobuf-gradle-plugin/issues/248. Please use files('path/to/directory') instead.
```