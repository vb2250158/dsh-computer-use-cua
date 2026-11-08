# DSH Cua Driver computer use

[中文](README.md)

Enable DSH's official native Cua Driver provider through a syncable configuration bundle. This package only declares dependencies and composition rows. It has no Host implementation, client, or build step. Official components own tools, permission handling, input delivery, screenshots, and teardown.

## Use

Install and enable this bundle in a DSH profile that supplies `tools` and `systemPrompt`; the standard Web profile already does. Record a full 40-character Git commit for this repository through the existing plugin synchronizer and install through the official installer. The shared third-party manifest records `dsh-computer-use-cua`, not its `@deepseek-ai/*` dependencies.

Disable other computer-use providers first, including the official macOS Computer Use bundle, Cua Driver MCP, and manually mounted native providers. This bundle uses its own stable row IDs and does not overwrite another bundle's rows. The official registry allows one provider and rejects conflicting activation; this package does not disable other plugins automatically.

Tools and guidance are registered at Host scope and inherited according to DSH's Agent scope rules. The bundle does not select a model or preset, change OS grants, or reserve the desktop for a session. Disabling it delegates tool withdrawal and driver shutdown to the official lifecycle. Input already delivered to an application cannot be rolled back. Sessions sharing the desktop must coordinate their operations.

## Permissions and screenshots

The DSH process needs a usable graphical desktop session and the permissions required by the target application. Windows integrity levels, application types, and background-input support can limit actions. A background refusal does not trigger a foreground retry or privilege elevation.

Model-visible screenshots require an attachment store and a model route that explicitly supports image input. Successful tool loading or permission checks do not prove screenshot admission, clicks, keyboard input, or window observation for the target application.

## Synchronization and versions

This package declares exact official dependency version `0.2.2-rc.1`. The native provider currently depends on Cua Driver `0.28.0`. Keep npm optional dependencies enabled for the platform's native runtime.

For source Web deployments, the synchronizer aligns official dependencies with the receiving machine's actual DSH checkout. This bundle's Git pin fixes its configuration, not another machine's official source or driver version. Verify resolved sources, versions, activation, and desktop behavior on each receiving machine. Do not publish machine-local source links in the shared plugin manifest.

## Validation scope

The declared Windows x64 environment with Node `24.15.0`, pnpm `11.28.5`, DSH `0.2.2-rc.1`, and Cua Driver `0.28.0` passed the official native SDK read-only e2e, isolated Web preview, enable/disable lifecycle, production activation, and shared-manifest publication checks. The driver discovered 56 tools and successfully listed visible windows. Both official components are active in production, with existing sessions preserved. The installed and shared runtime remains pinned to `b293c1c446c1437cfd304ea7b9924f2fb3f0754c`; this later documentation commit does not change runtime configuration. Screenshots, mouse/keyboard input, model calls, and other machines remain unverified. Receiving machines use the existing synchronizer to check for updates and pull/apply, then verify local activation and desktop permissions. See [tested-environment.json](tested-environment.json).

See [DSH Computer use](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/subsystems/computer-use.md) and [Cua Driver 0.28.0](https://github.com/trycua/cua/tree/cua-driver-rs-v0.28.0/libs/cua-driver) for official behavior and limitations. Official dependencies retain their authors and licenses. Repository visibility is managed separately from this package metadata.

## License

Original general-purpose plugin code and configuration in this repository are licensed under [MIT](LICENSE). Official DSH, Cua Driver and other external dependencies retain their own copyrights and licenses; this license does not relicense them. `private: true` prevents accidental npm publication and does not declare GitHub repository visibility. Runtime configuration, credentials, sessions and user media are outside this source package.
