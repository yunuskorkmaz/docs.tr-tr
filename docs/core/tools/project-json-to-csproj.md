---
title: Project.JSON ile csproj karşılaştırması - .NET Core
description: Project.json ile csproj öğeleri arasında bir eşleme bakın.
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.openlocfilehash: 0079164470f87df665be6f9de62bc98d3fb51696
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45744033"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Project.json ile csproj özellikleri arasında bir eşleme

Tarafından [Nate McMaster](https://github.com/natemcmaster)

.NET Core araçları geliştirme sırasında artık desteklemek için bir önemli tasarım değişikliğin yapıldığı *project.json* dosyaları ve bunun yerine .NET Core projeleri için MSBuild/csproj biçimine taşıyın.

Bu makale nasıl ayarlarında *project.json* yeni biçimini kullanın ve projenize yükseltirken yükseltme araçları tarafından yapılan değişiklikleri anlama hakkında bilgi edinmek için MSBuild/csproj biçimde temsil edilir araç en son sürümü.

## <a name="the-csproj-format"></a>Csproj biçimine

Yeni biçim \*.csproj, XML tabanlı bir biçim olduğu. Aşağıdaki örnek, gösterir kullanarak bir .NET Core proje kök düğümü `Microsoft.NET.Sdk`. Web projeleri için kullanılan SDK şeklindedir `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Ortak bir üst düzey özellikler

### <a name="name"></a>name

```json
{
  "name": "MyProjectName"
}
```

Artık desteklenmiyor. Csproj Bu dizin adıyla tanımlanan proje dosya adına göre belirlenir. Örneğin, `MyProjectName.csproj`.

Varsayılan olarak, proje dosya adına ayrıca değerini belirtir. `<AssemblyName>` ve `<PackageId>` özellikleri.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>` Değerinden farklı bir değere sahip `<PackageId>` varsa `buildOptions\outputName` özelliği, project.json içinde tanımlandı.
Daha fazla bilgi için [diğer ortak yapı seçeneklerini](#other-common-build-options).

### <a name="version"></a>sürüm

```json
{
  "version": "1.0.0-alpha-*"
}
```

Kullanım `VersionPrefix` ve `VersionSuffix` özellikleri:

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

Ayrıca `Version` özelliği, ancak bu geçersiz sürüm ayarlarını paketleme sırasında:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Diğer ortak kök düzeyinde seçenekleri

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a>Çerçeveler

### <a name="one-target-framework"></a>Bir hedef çerçeve

```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a>Birden çok hedef çerçeve

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Kullanım `TargetFrameworks` hedef çerçeve listesini tanımlamak için özellik. Framework değerleri birbirinden ayırmak için noktalı virgül kullanın.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>bağımlılıklar

> [!IMPORTANT]
> Bağımlılık ise bir **proje** ve bir paket biçimi farklıdır.
> Daha fazla bilgi için [bağımlılık türü](#dependency-type) bölümü.

### <a name="netstandardlibrary-metapackage"></a>NETStandard.Library metapackage

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a>Microsoft.NETCore.App metapackage

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

Unutmayın `<RuntimeFrameworkVersion>` geçirilen Proje değeri, SDK'sı yüklü olan sürümü tarafından belirlenir.

### <a name="top-level-dependencies"></a>Üst düzey bağımlılıkları

```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a>Çerçeve başına bağımlılıklarını

```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a>içeri aktarmalar

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a>Bağımlılık türü

#### <a name="type-project"></a>Tür: Proje

```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> Bu şekilde çalışmamasına neden olur, `dotnet pack --version-suffix $suffix` bir proje başvurusu bağımlılık sürümünü belirler.

#### <a name="type-build"></a>Tür: derleme

```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a>Tür: platform

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

Csproj'a eşdeğeri yoktur.

## <a name="runtimes"></a>Çalışma zamanları

```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a>Tek başına uygulamaları (müstakil dağıtım)

Project.json'da, tanımlayan bir `runtimes` uygulama olan sırasında tek başına bölüm anlamına gelir oluşturun ve yayınlayın.
Msbuild'de, tüm projeleri, *taşınabilir* yapı sırasında ancak bağımsız yayımlanabilir.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Daha fazla bilgi için [müstakil dağıtımlar (SCD)](../deploying/index.md#self-contained-deployments-scd).

## <a name="tools"></a>araçlar

```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> `imports` Araçları csproj içinde desteklenmez. İçeri aktarmalar gereken Araçlar yeni çalışmaz `Microsoft.NET.Sdk`.

## <a name="buildoptions"></a>buildOptions

Ayrıca bkz: [dosyaları](#files).

### <a name="emitentrypoint"></a>emitEntryPoint

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Varsa `emitEntryPoint` olduğu `false`, değerini `OutputType` dönüştürülür `Library`, varsayılan değer olan:

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a>KeyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

`keyFile` Üç özellik msbuild'de öğe genişletir:

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a>Diğer ortak derleme seçenekleri

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a>packOptions

Ayrıca bkz: [dosyaları](#files).

### <a name="common-pack-options"></a>Ortak paketi seçenekleri

```json
{
  "packOptions": {
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

İçin eşdeğeri yoktur `owners` msbuild'de öğe.
İçin `summary`, MSBuild kullanabilirsiniz `<Description>` özelliği olsa bile değerini `summary` bu özellik eşlendiği olduğundan bu özellik için otomatik olarak taşınmaz [ `description` ](#other-common-root-level-options) öğesi.

## <a name="scripts"></a>betikler

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

MSBuild eşdeğeri olan [hedefleri](/visualstudio/msbuild/msbuild-targets):

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a>runtimeOptions

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

Bu gruptaki "System.GC.Server" özelliği dışında tüm ayarlar adlı bir dosyaya yerleştirilir *runtimeconfig.template.json* proje klasöründeki kök nesnesi için geçiş işlemi sırasında yükseltilmiş seçenekleri:

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

"System.GC.Server" özelliği csproj dosyasına geçirilir:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Ancak, bu değerleri csproj yanı sıra MSBuild özellikleri ayarlayabilirsiniz:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a>shared

```json
{
  "shared": "shared/**/*.cs"
}
```

Csproj içinde desteklenmiyor. Bunun yerine oluşturmalısınız içerik dosyalarına dahil, *.nuspec* dosya.
Daha fazla bilgi için [içerik dosyaları dahil olmak üzere](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>dosyaları

İçinde *project.json*, derleme ve paketi genişletilmiş derlenip başka klasörlerinden ekleme.
Msbuild'de yapıldığını kullanarak [öğeleri](/visualstudio/msbuild/common-msbuild-project-items). Aşağıdaki örnek bir ortak bir dönüştürmedir:

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> Varsayılan birçok [Glob desenlerinin](https://en.wikipedia.org/wiki/Glob_(programming)) .NET Core SDK'sı tarafından otomatik olarak eklenir.
> Daha fazla bilgi için [varsayılan derleme öğe değerleri](https://aka.ms/sdkimplicititems).

Tüm MSBuild `ItemGroup` öğeleri Destek `Include`, `Exclude`, ve `Remove`.

Paket düzeni .nupkg içinde değiştirilebilir `PackagePath="path"`.

Dışında `Content`, açıkça ekleme çoğu öğesi grupları iste `Pack="true"` pakete dahil edilecek. `Content` yerleştirilir *içeriği* MSBuild sonrasında bir paket klasörüne `<IncludeContentInPack>` özelliği `true` varsayılan olarak.
Daha fazla bilgi için [bir içerik paketine](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"` Proje göreli dosya yolu için paket yolu ayarlama, kısa bir yoludur.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xUnit

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a>MSTest

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca Bkz.

* [CLI değişiklikleri üst düzey genel bakış](../tools/cli-msbuild-architecture.md)
