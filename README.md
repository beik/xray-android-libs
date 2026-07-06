# Xray Android Libraries

Android 平台的 Xray-core 预编译库，通过 GitHub Packages 分发。

## 包含的库

### xray-core

Xray-core 预编译二进制文件，打包为 AAR 格式。

**支持的架构：**
- arm64-v8a (ARM 64位)
- x86_64 (如果可用)

**包含的文件：**
- `libxray.so` - Xray 可执行文件
- `geoip.dat` - GeoIP 数据库
- `geosite.dat` - GeoSite 数据库

## 使用方法

### 1. 配置 Maven 仓库

在项目的 `android/build.gradle.kts` 中添加：

```kotlin
allprojects {
    repositories {
        google()
        mavenCentral()
        maven {
            name = "GitHubPackages"
            url = uri("https://maven.pkg.github.com/beik/xray-android-libs")
            credentials {
                username = project.findProperty("gpr.user") 
                    ?: System.getenv("GITHUB_ACTOR")
                password = project.findProperty("gpr.key") 
                    ?: System.getenv("GITHUB_TOKEN")
            }
        }
    }
}
```

### 2. 添加依赖

在模块的 `build.gradle.kts` 中添加：

```kotlin
dependencies {
    implementation("com.zeroping:xray-core:26.3.27")
}
```

### 3. 配置 GitHub 认证

创建 `~/.gradle/gradle.properties`：

```properties
gpr.user=your-github-username
gpr.key=your-github-token
```

**注意：** GitHub Token 需要 `read:packages` 权限。

## 发布新版本

1. 进入 Actions 页面
2. 选择 "Publish Xray-core to GitHub Packages"
3. 点击 "Run workflow"
4. 输入版本号（如 `26.3.27`）
5. 点击 "Run workflow"

## 版本历史

- `26.3.27` - 初始版本

## 许可证

- Xray-core: GNU General Public License v3.0
- 本仓库: MIT License

## 相关链接

- [Xray-core 官方仓库](https://github.com/XTLS/Xray-core)
- [GitHub Packages 文档](https://docs.github.com/en/packages)
