# PrivacyManifest

PrivacyManifest is the pkl file that provides the benefits of static typing to generate [Apple's xcprivacy file](https://developer.apple.com/documentation/bundleresources/privacy_manifest_files/describing_data_use_in_privacy_manifests).

## Installation

Packages within this repository are published as `package://pkg.pkl-lang.org/github.com/fumito-ito/PrivacyManifest@<VERSION>`.

### Direct imports

Modules from package can be imported directly. For example, the below line imports the module from package at version `0.0.1`:

```pkl
import "package://pkg.pkl-lang.org/github.com/fumito-ito/PrivacyManifest/PrivacyManifest@0.0.1"
```

## Usage

create your pkl file to generate `xcprivacy` file.

```pkl
amends "package://pkg.pkl-lang.org/github.com/fumito-ito/PrivacyManifest/PrivacyManifest@0.0.1#/PrivacyManifestFile.pkl"

NSPrivacyTracking = true
NSPrivacyTrackingDomains {
    "com.github.fumito-ito.PrivacyManifest.pkl"
}
```

... and generate !

```sh
$ pkl eval -f plist YourPklFile.pkl > PrivacyInfo.xcprivacy
```

## Validation

This module provides following validations.

### Number of NSPrivacyTrackingDomains

If `NSPrivacyTracking = true`, `NSPrivacyTrackingDomains` needs one or more domains.

### Domain style

`NSPrivacyTrackingDomains` should be domain style string, e.g. `com.example.app`

### Combination of `NSPrivacyAccessedAPIType` and `NSPrivacyAccessedAPITypeReasons`

`NSPrivacyAccessedAPITypeReasons` should supply the relevant values from `NSPrivacyAccessedAPIType`.

### Name checking

Check that the correct names are used for the classes listed below.

- NSPrivacyAccessedAPIType
- NSPrivacyAccessedAPITypeReasons
- NSPrivacyCollectedDataType
- NSPrivacyCollectedDataTypePurposes

## Dependencies

[Pkl 0.25.2](https://github.com/apple/pkl)

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[Apache License 2.0](https://choosealicense.com/licenses/apache-2.0/)
