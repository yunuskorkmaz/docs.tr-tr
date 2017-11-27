---
title: "Project.JSON ve csproj karşılaştırması - .NET Core"
description: "Project.json ve csproj öğeleri arasında bir eşleme bakın."
keywords: Project.JSON, csproj, .NET Core, MSBuild
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 79c50621-a24a-4e64-bbb9-b953113e841c
ms.openlocfilehash: 0f82e82c6a11220e24c85cef19bc131e12c77bf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Project.json ve csproj özellikleri arasında bir eşleme

Tarafından [Can Etikan McMaster](https://github.com/natemcmaster)

.NET Core araç geliştirme sırasında artık desteklemek için bir önemli tasarım değişikliğin yapıldığı *project.json* dosyaları ve bunun yerine .NET Core projeleri MSBuild/csproj biçimine taşıyın.

Bu makalede gösterilmektedir nasıl ayarlarında *project.json* yeni biçimini kullanın ve projenize yükseltirken geçiş araçları tarafından yapılan değişiklikleri anlama hakkında bilgi için MSBuild/csproj biçiminde gösterilir araç en son sürümü. 
 
## <a name="the-csproj-format"></a>Csproj biçimi

Yeni biçim \*.csproj, XML tabanlı bir biçim değil. Aşağıdaki örnek, .NET Core kullanarak proje kök düğümü gösterir `Microsoft.NET.Sdk`. Web projeleri için kullanılan SDK olduğu `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Ortak üst düzey özellikleri

### <a name="name"></a>name
```json
{
  "name": "MyProjectName"
}
```

Artık desteklenmemektedir. Csproj içinde bu dizin adıyla tanımlanan proje filename tarafından belirlenir. Örneğin, `MyProjectName.csproj`.

Varsayılan olarak, proje filename de değerini belirtir. `<AssemblyName>` ve `<PackageId>` özellikleri. 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>` Farklı bir değere sahip olur `<PackageId>` varsa `buildOptions\outputName` özelliği, project.json tanımlanmıştı. Daha fazla bilgi için bkz: [başka bir genel derleme seçenekleri](#other-common-build-options).

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

Aynı zamanda `Version` özelliği, ancak bu ayarları geçersiz kılar sürüm paketlemesi sırasında:

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

## <a name="frameworks"></a>çerçeveler

### <a name="one-target-framework"></a>Bir hedef framework
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

### <a name="multiple-target-frameworks"></a>Birden çok hedef çerçeveyi

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Kullanım `TargetFrameworks` hedef çerçeveyi listesini tanımlamak için özellik. Birden çok framework değerleri ayırmak için noktalı virgül kullanın. 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>bağımlılıklar

> [!IMPORTANT]
> Bağımlılık ise bir **proje** ve bir paket biçimi farklıdır. Daha fazla bilgi için bkz: [bağımlılık türü](#dependency-type) bölümü.

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

Unutmayın `<RuntimeFrameworkVersion>` değeri geçirilen projesinde yüklü olan SDK sürümü tarafından belirlenir.

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

### <a name="per-framework-dependencies"></a>Çerçeve başına bağımlılıkları
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
> Bu şekilde kesilir, `dotnet pack --version-suffix $suffix` proje başvurusu bağımlılık sürümünü belirler.


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

İçinde csproj eşdeğeri yoktur. 

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

### <a name="standalone-apps-self-contained-deployment"></a>Tek başına uygulamaları (kendi içinde bulunan bir dağıtım)
Project.JSON tanımlayan bir `runtimes` uygulama edildi sırasında tek başına bölüm anlamına gelir oluşturma ve yayımlama.
MSBuild tüm projeleri olan *taşınabilir* derleme, ancak tek başına olarak yayımlanabilir.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Daha fazla bilgi için bkz: [müstakil dağıtımları (SCD)](../deploying/index.md#self-contained-deployments-scd).

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
> `imports`Araçlar ' csproj desteklenmez. İçeri aktarmalar gereken araçları yeni çalışmaz `Microsoft.NET.Sdk`.

## <a name="buildoptions"></a>buildOptions

Ayrıca bkz. [dosyaları](#files).

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

Varsa `emitEntryPoint` olan `false`, değeri `OutputType` dönüştürülür `Library`, varsayılan değer olan:

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

### <a name="keyfile"></a>keyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

`keyFile` Öğesi genişletir MSBuild üç özelliklerinde için:

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

Ayrıca bkz. [dosyaları](#files).

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

İçin bir eşdeğeri yoktur `owners` MSBuild öğesinde. İçin `summary`, MSBuild kullanabilirsiniz `<Description>` özelliği, olsa bile değerini `summary` bu özelliği bu yana otomatik olarak bu özelliğe geçirilmez [ `description` ](#-other-common-root-level-options) öğesi.

## <a name="scripts"></a>betikler

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Kendi eşdeğerdir msbuild'de [hedefleri](/visualstudio/msbuild/msbuild-targets):

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

Bu gruptaki "System.GC.Server" özellik dışında tüm ayarlar adlı bir dosyaya yerleştirilir *runtimeconfig.template.json* proje klasöründeki kök nesnesine geçiş işlemi sırasında kaldırılmış seçeneklerle:

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

Csproj içinde desteklenmez. Bunun yerine oluşturmalısınız içerik dosyalarına eklemek, *.nuspec* dosya. Daha fazla bilgi için bkz: [içerik dosyaları dahil olmak üzere](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>dosyaları

İçinde *project.json*, yapı ve paketi genişletilmiş derlemek ve farklı klasörlerden katıştırmak için.
MSBuild içinde bu yapılır kullanarak [öğeleri](/visualstudio/msbuild/common-msbuild-project-items). Aşağıdaki örnek, ortak bir dönüştürme verilmiştir:

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
> Varsayılan birçok [genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) .NET Core SDK'sı tarafından otomatik olarak eklenir.
> Daha fazla bilgi için bkz: [varsayılan derleme öğesi değerleri](https://aka.ms/sdkimplicititems).

Tüm MSBuild `ItemGroup` öğeleri Destek `Include`, `Exclude`, ve `Remove`.

Paket düzeni .nupkg içinde ile değiştirilebilir `PackagePath="path"`.

Dışında `Content`, çoğu öğesi gruplarını açıkça ekleme gerektiren `Pack="true"` pakete dahil edilecek. `Content`işaretleneceğini belirtilir *içerik* MSBuild itibaren bir paket klasörüne `<IncludeContentInPack>` özelliği ayarlanmış `true` varsayılan olarak. Daha fazla bilgi için bkz: [bir paketteki içerik dahil olmak üzere](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"`Proje göreli dosya yolu paket yolu ayarlama kısa bir yoludur.

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

[CLI değişiklikleri üst düzey genel bakış](../tools/cli-msbuild-architecture.md)
