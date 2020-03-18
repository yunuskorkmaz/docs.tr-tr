---
title: project.json ve csproj karşılaştırması
description: Project.json ve csproj öğeleri arasında bir eşleme bakın.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: abe515007b47b415ac33e3350a29edced1784d68
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451111"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>project.json ve csproj özellikleri arasında bir haritalama

Yazar: [Nate McMaster](https://github.com/natemcmaster)

.NET Core takımlamanın geliştirilmesi sırasında, *project.json* dosyalarını artık desteklememek ve bunun yerine .NET Core projelerini MSBuild/csproj biçimine taşımak için önemli bir tasarım değişikliği yapıldı.

Bu makalede, *project.json'daki* ayarların MSBuild/csproj formatında nasıl temsil edildiği gösterilmektedir, böylece yeni biçimi nasıl kullanacağınızı öğrenebilir ve projenizi araçlamanın en son sürümüne yükseltirken geçiş araçları tarafından yapılan değişiklikleri anlayabilirsiniz.

## <a name="the-csproj-format"></a>Csproj formatı

Yeni biçim, \*.csproj, XML tabanlı bir biçimdir. Aşağıdaki örnekte .NET Core projesinin kök düğümünü kullanarak `Microsoft.NET.Sdk`. Web projeleri için Kullanılan SDK' dır. `Microsoft.NET.Sdk.Web`

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Ortak üst düzey özellikler

### <a name="name"></a>ad

```json
{
  "name": "MyProjectName"
}
```

Artık desteklenmiå. Csproj'da bu, genellikle dizin adı ile eşleşen proje dosya adı tarafından belirlenir. Örneğin, `MyProjectName.csproj`.

Varsayılan olarak, proje dosya adı da ve `<AssemblyName>` `<PackageId>` özelliklerideğerini belirtir.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

Özellik `<AssemblyName>` project.json'da `buildOptions\outputName` tanımlanmışsa, `<PackageId>` farklı bir değere sahip olacaktır.
Daha fazla bilgi için [bkz.](#other-common-build-options)

### <a name="version"></a>version

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

`Version` Özelliği de kullanabilirsiniz, ancak bu, paketleme sırasında sürüm ayarlarını geçersiz kılabilir:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Diğer ortak kök düzeyi seçenekleri

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

## <a name="frameworks"></a>Çerçeve

### <a name="one-target-framework"></a>Tek hedef çerçeve

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

Hedef `TargetFrameworks` çerçeveler listenizi tanımlamak için özelliği kullanın. Birden çok çerçeve değerlerini ayırmak için yarı iki nokta üst üste kullanın.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>bağımlılıklar

> [!IMPORTANT]
> Bağımlılık bir paket değil, bir **projeyse,** biçim farklıdır.
> Daha fazla bilgi için [bağımlılık türü](#dependency-type) bölümüne bakın.

### <a name="netstandardlibrary-metapackage"></a>NETStandard.Library metapaketi

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

### <a name="microsoftnetcoreapp-metapackage"></a>Microsoft.NETCore.App metapaketi

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

Geçirilen projedeki değerin `<RuntimeFrameworkVersion>` yüklediğiniz SDK sürümütarafından belirlendiğini unutmayın.

### <a name="top-level-dependencies"></a>Üst düzey bağımlılıklar

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

### <a name="per-framework-dependencies"></a>Çerçeve başına bağımlılıklar

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

### <a name="dependency-type"></a>bağımlılık türü

#### <a name="type-project"></a>türü: proje

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
> Bu, proje başvurusu `dotnet pack --version-suffix $suffix` bağımlılık sürümünü belirleyen yolu kıracak.

#### <a name="type-build"></a>türü: yapı

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

#### <a name="type-platform"></a>türü: platform

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

Csproj'da eşdeğeri yoktur.

## <a name="runtimes"></a>Çalıştırma

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

### <a name="standalone-apps-self-contained-deployment"></a>Bağımsız uygulamalar (bağımsız dağıtım)

Project.json'da, bir `runtimes` bölümü tanımlamak, uygulamanın yapı ve yayımlama sırasında tek başına olduğu anlamına gelir.
MSBuild'te, tüm projeler yapı sırasında *taşınabilirdir,* ancak bağımsız olarak yayınlanabilir.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Daha fazla bilgi için [bkz.](../deploying/index.md#publish-self-contained)

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
> `imports`araçlar da csproj desteklenmez. İthalat gerektiren araçlar yeni `Microsoft.NET.Sdk`ile çalışmaz.

## <a name="buildoptions"></a>buildOptions

Ayrıca [Bakınız Dosyalar](#files).

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

Ise `emitEntryPoint` `false`, değeri `OutputType` varsayılan değer `Library`olan , dönüştürülür:

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

### <a name="keyfile"></a>Keyfile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

Öğe `keyFile` MSBuild üç özelliklere genişletir:

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a>Diğer ortak yapı seçenekleri

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

Ayrıca [Bakınız Dosyalar](#files).

### <a name="common-pack-options"></a>Ortak paket seçenekleri

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

MSBuild'teki öğenin eşdeğeri `owners` yoktur.
Çünkü, `summary`değeri `<Description>` `summary` bu özelliğe otomatik olarak geçirilemese de, bu özellik [`description`](#other-common-root-level-options) öğeye eşlenmiş olduğundan, MSBuild özelliğini kullanabilirsiniz.

## <a name="scripts"></a>betikler

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

MSBuild onların eşdeğer [hedefleri](/visualstudio/msbuild/msbuild-targets)şunlardır:

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

"System.GC.Server" özelliği dışında bu gruptaki tüm ayarlar, proje klasöründe *runtimeconfig.template.json* adlı bir dosyaya yerleştirilir ve geçiş işlemi sırasında seçenekler kök nesneye kaldırılır:

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

"System.GC.Server" özelliği csproj dosyasına taşınır:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Ancak, csproj yanı sıra MSBuild özellikleri tüm bu değerleri ayarlayabilirsiniz:

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

Csproj desteklenmez. Bunun yerine *.nuspec* dosyanıza içerik dosyaları eklemeniz gerekir.
Daha fazla bilgi için [bkz.](/nuget/schema/nuspec#including-content-files)

## <a name="files"></a>files

*Project.json,* build ve pack farklı klasörlerden derlemek ve katıştırmak için genişletilebilir.
MSBuild'te bu öğeler [kullanılarak](/visualstudio/msbuild/common-msbuild-project-items)yapılır. Aşağıdaki örnek, yaygın bir dönüşümdür:

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
> Varsayılan [globbing desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) çoğu otomatik olarak .NET Core SDK tarafından eklenir.
> Daha fazla bilgi için [bkz.](https://aka.ms/sdkimplicititems)

`ItemGroup` Tüm MSBuild `Include`elemanları `Exclude`destek `Remove`, ve .

.nupkg içindeki paket düzeni `PackagePath="path"`.

Bunun `Content`dışında, çoğu öğe grubu `Pack="true"` pakete eklenmesi için açıkça eklenmesini gerektirir. `Content`MSBuild `<IncludeContentInPack>` özelliği varsayılan olarak ayarlı `true` *olduğundan,* bir paketteki içerik klasörüne konulacaktır.
Daha fazla bilgi için [bkz.](/nuget/schema/msbuild-targets#including-content-in-a-package)

`PackagePath="%(Identity)"`proje ile ilgili dosya yoluna paket yolu ayarlamanın kısa bir yoludur.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xBirim

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

## <a name="see-also"></a>Ayrıca bkz.

- [CLI'deki değişikliklere üst düzey genel bakış](../tools/cli-msbuild-architecture.md)
