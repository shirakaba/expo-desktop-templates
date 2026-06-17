# Expo Desktop Templates

This is the repo for all the app templates and library templates used by [Expo Desktop](https://github.com/shirakaba/expo-desktop).

## File structure

```
├── app                  ## App templates ##
│   └── blank-typescript # … Based on expo-template-blank-typescript
│       └── 0.81         # … For react-native@0.81
│
└── lib                  ## Library templates ##
                         # (TODO)
```

## Approach to creating desktop-friendly templates

To create a desktop-friendly Expo template for a given version of React Native, say, `0.81`, I search up and down different version branches (e.g. `sdk-54`, `sdk-55`…) of `expo-template-bare-minimum` to look for the one that references `react-native@0.81` in its `package.json`, and then use that SDK version as my target one.

But, as per the name, that's only the "bare minimum" template. It's mainly just to provide the `ios` and `android` folders, and is underdeveloped in other areas like the `app.json`. So I actually create my templates based on the more developed `expo-template-blank-typescript`, then take the `ios` and `android` folders from `expo-template-bare-minimum`. This is essentially what the Expo CLI does (you create from a different template to the one you prebuild from). For Expo Desktop, though, we'll create and prebuild from the same template. This simplifies things, as there's a single source of truth for common files like the `package.json`.

Once we've melded together `blank-typescript` and `bare-minimum`, we then merge in the `react-native-macos` and `react-native-windows` templates. This is mostly a case of just dragging in the `macos` and `windows` folders, but there are also some straggler files (`NuGet_Config` and `jest.config.windows.js`) in the Windows case. I actually use the latest templates from `main`, rather than a versioned branch, because the benefits from getting the latest version of the templates (which have historically fixed things like CocoaPods setup and MSBuild config) very much outweigh the low risk of the template only working properly on newer React Native versions.

## References

- Expo templates, used by `create-expo-app` and `expo prebuild`:
  - `bare-minimum`:
    - [SDK 53](https://github.com/expo/expo/tree/sdk-53/templates/expo-template-bare-minimum)
    - [SDK 54](https://github.com/expo/expo/tree/sdk-54/templates/expo-template-bare-minimum)
    - [SDK 55](https://github.com/expo/expo/tree/sdk-55/templates/expo-template-bare-minimum)
    - [SDK 56](https://github.com/expo/expo/tree/sdk-56/templates/expo-template-bare-minimum)
    - [`main`](https://github.com/expo/expo/tree/main/templates/expo-template-bare-minimum)
  - `blank-typescript`:
    - [SDK 53](https://github.com/expo/expo/tree/sdk-53/templates/expo-template-blank-typescript)
    - [SDK 54](https://github.com/expo/expo/tree/sdk-54/templates/expo-template-blank-typescript)
    - [SDK 55](https://github.com/expo/expo/tree/sdk-55/templates/expo-template-blank-typescript)
    - [SDK 56](https://github.com/expo/expo/tree/sdk-56/templates/expo-template-blank-typescript)
    - [`main`](https://github.com/expo/expo/tree/main/templates/expo-template-blank-typescript)
- React Native templates, used by `@react-native-community/cli init`:
  - `HelloWorld`:
    - [`0.81-stable`](https://github.com/react/react-native/tree/0.81-stable/private/helloworld)
    - [`0.82-stable`](https://github.com/react/react-native/tree/0.82-stable/private/helloworld)
    - [`0.83-stable`](https://github.com/react/react-native/tree/0.83-stable/private/helloworld)
    - [`0.84-stable`](https://github.com/react/react-native/tree/0.84-stable/private/helloworld)
    - [`0.85-stable`](https://github.com/react/react-native/tree/0.85-stable/private/helloworld)
    - [`0.86-stable`](https://github.com/react/react-native/tree/0.86-stable/private/helloworld)
    - [`main`](https://github.com/react/react-native/tree/main/private/helloworld)
- React Native macOS templates, used by `react-native-macos-init`:
  - `HelloWorld`:
    - [`0.81-stable`](https://github.com/microsoft/react-native-macos/tree/0.81-stable/packages/react-native/local-cli/generator-macos/templates/macos)
    - [`main`](https://github.com/microsoft/react-native-macos/tree/main/packages/react-native/local-cli/generator-macos/templates/macos)
- React Native Windows templates, used by `react-native init-windows`:
  - `cpp-app`:
    - [`0.81-stable`](https://github.com/microsoft/react-native-windows/tree/0.81-stable/vnext/templates/cpp-app)
    - [`0.82-stable`](https://github.com/microsoft/react-native-windows/tree/0.82-stable/vnext/templates/cpp-app)
    - [`0.83-stable`](https://github.com/microsoft/react-native-windows/tree/0.83-stable/vnext/templates/cpp-app)
    - [`0.84-stable`](https://github.com/microsoft/react-native-windows/tree/0.84-stable/vnext/templates/cpp-app)
    - [`main`](https://github.com/microsoft/react-native-windows/tree/main/vnext/templates/cpp-app)
  - `cpp-lib`:
    - [`0.81-stable`](https://github.com/microsoft/react-native-windows/tree/0.81-stable/vnext/templates/cpp-lib)
    - [`0.82-stable`](https://github.com/microsoft/react-native-windows/tree/0.82-stable/vnext/templates/cpp-lib)
    - [`0.83-stable`](https://github.com/microsoft/react-native-windows/tree/0.83-stable/vnext/templates/cpp-lib)
    - [`0.84-stable`](https://github.com/microsoft/react-native-windows/tree/0.84-stable/vnext/templates/cpp-lib)
    - [`main`](https://github.com/microsoft/react-native-windows/tree/main/vnext/templates/cpp-lib)
