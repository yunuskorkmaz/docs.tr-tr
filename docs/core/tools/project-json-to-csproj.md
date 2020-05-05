---
title: Project. JSON ve csproj karşılaştırması
description: Project. JSON ve csproj öğeleri arasındaki eşlemeyi görüntüleyin.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: feaa7e9cde7e1aa4dfe94d699b14a018fc728f27
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794630"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Project. JSON ve csproj özellikleri arasındaki eşleme

[Nate McMaster](https://github.com/natemcmaster) tarafından

.NET Core araçları 'nın geliştirilmesi sırasında, artık *Project. JSON* dosyalarını desteklemeyen önemli bir tasarım değişikliği yapılmıştır ve bunun yerine .NET Core projelerini MSBuild/csproj biçimine taşıyın.

Bu makalede, Project *. JSON* Içindeki ayarların MSBuild/csproj biçiminde nasıl temsil edildiği gösterilmektedir, böylece yeni biçimin nasıl kullanılacağını ve projenizi araçların en son sürümüne yükseltirken geçiş araçlarının yaptığı değişiklikleri nasıl anlayabileceğinizi öğrenebilirsiniz.

## <a name="the-csproj-format"></a>Csproj biçimi

Yeni biçim olan \*. csproj, XML tabanlı bir biçimdir. Aşağıdaki örnek, `Microsoft.NET.Sdk`kullanarak bir .NET Core projesinin kök düğümünü gösterir. Web projeleri için kullanılan SDK `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Ortak en üst düzey Özellikler

### <a name="name"></a>ad

```json
{
  "name": "MyProjectName"
}
```

Artık desteklenmiyor. Csproj içinde, bu, genellikle dizin adıyla eşleşen proje dosya adı tarafından belirlenir. Örneğin, `MyProjectName.csproj`.

Varsayılan olarak, proje dosya adı `<AssemblyName>` ve `<PackageId>` özelliklerinin değerini de belirtir.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

, `<AssemblyName>` `buildOptions\outputName` Property, Project. JSON içinde `<PackageId>` tanımlananla farklı bir değere sahip olacaktır.
Daha fazla bilgi için bkz. [diğer ortak derleme seçenekleri](#other-common-build-options).

### <a name="version"></a>version

```json
{
  "version": "1.0.0-alpha-*"
}
```

`VersionPrefix` Ve `VersionSuffix` özelliklerini kullanın:

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

`Version` Özelliğini de kullanabilirsiniz, ancak bu durum paketleme sırasında sürüm ayarlarını geçersiz kılabilir:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Diğer genel kök düzeyi seçenekleri

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

## <a name="frameworks"></a>çerçeveleri

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

Hedef çerçeveler `TargetFrameworks` listenizi tanımlamak için özelliğini kullanın. Birden çok Framework değerini ayırmak için noktalı virgül kullanın.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>bağımlılıklar

> [!IMPORTANT]
> Bağımlılık bir paket değil bir **projem** ise, biçim farklıdır.
> Daha fazla bilgi için [bağımlılık türü](#dependency-type) bölümüne bakın.

### <a name="netstandardlibrary-metapackage"></a>NETStandard. Library meta paketi

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

### <a name="microsoftnetcoreapp-metapackage"></a>Microsoft. NETCore. app metapackage

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

Geçirilen projedeki `<RuntimeFrameworkVersion>` değerin, yüklediğiniz SDK sürümü tarafından belirlendiğini unutmayın.

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

#### <a name="type-project"></a>Tür: proje

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
> Bu, bir proje başvurusunun bağımlılık `dotnet pack --version-suffix $suffix` sürümünü belirleyen yolunu ortadan keser.

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

Csproj içinde eşdeğer değildir.

## <a name="runtimes"></a>zamanları

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

### <a name="standalone-apps-self-contained-deployment"></a>Tek başına uygulamalar (otomatik olarak kapsanan dağıtım)

Project. json ' de bir `runtimes` bölüm tanımlamak, uygulamanın oluşturma ve yayımlama sırasında tek başına olduğu anlamına gelir.
MSBuild 'de, tüm projeler derleme sırasında *Taşınabilir* , ancak tek başına olarak yayımlanabilir.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Daha fazla bilgi için bkz. [kendi içindeki dağıtımlar (SCD)](../deploying/index.md#publish-self-contained).

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
> `imports`Açık araçlar, csproj 'da desteklenmez. İçeri aktarmaları gereken araçlar yeni `Microsoft.NET.Sdk`ile çalışmaz.

## <a name="buildoptions"></a>Buildoseçenekleri

Ayrıca bkz. [dosyalar](#files).

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

Was `emitEntryPoint` `false`ise değeri `OutputType` , varsayılan değer olan değerine dönüştürülür `Library`:

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

### <a name="keyfile"></a>Dosyasına

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

`keyFile` Öğe MSBuild 'te üç özelliğe genişletilir:

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

Ayrıca bkz. [dosyalar](#files).

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

MSBuild içindeki `owners` öğe için eşdeğer yok.
İçin `summary`, bu özellik `<Description>` `summary` [`description`](#other-common-root-level-options) öğesiyle eşlendiğinden, değeri bu özelliğe otomatik olarak geçirilmese de, MSBuild özelliğini kullanabilirsiniz.

## <a name="scripts"></a>betikler

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

MSBuild 'teki eşdeğeri [hedefler](/visualstudio/msbuild/msbuild-targets):

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

Bu gruptaki "System. GC. Server" özelliği hariç tüm ayarlar, proje klasöründe *runtimeconfig. Template. JSON* adlı bir dosyaya yerleştirilir ve bu işlem, geçiş işlemi sırasında kök nesnesine yükseltilmemiş seçenekleridir:

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

"System. GC. Server" özelliği csproj dosyasına geçirilir:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Bununla birlikte, csproj içindeki tüm değerleri ve MSBuild özelliklerini de ayarlayabilirsiniz:

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

Csproj içinde desteklenmez. Bunun yerine, *. nuspec* dosyanızdaki içerik dosyalarını ekle ' nin oluşturulması gerekir.
Daha fazla bilgi için bkz. [içerik dosyaları ekleme](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>files

*Project. JSON*içinde derleme ve paketleme farklı klasörlerden derlenmesi ve katıştırılması için genişletilebilir.
MSBuild 'te bu, [öğeler](/visualstudio/msbuild/common-msbuild-project-items)kullanılarak yapılır. Aşağıdaki örnek ortak bir dönüştürmedir:

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
> Varsayılan [Glob desenlerinin](https://en.wikipedia.org/wiki/Glob_(programming)) birçoğu .NET Core SDK tarafından otomatik olarak eklenir.
> Daha fazla bilgi için bkz. [varsayılan derleme öğesi değerleri](https://aka.ms/sdkimplicititems).

Tüm MSBuild `ItemGroup` öğeleri, `Include` `Exclude`, ve `Remove`destekler.

. Nupkg içindeki paket düzeni ile `PackagePath="path"`değiştirilebilir.

Dışında `Content`, çoğu öğe grubu pakete dahil etmek için `Pack="true"` açıkça ekleme gerektirir. `Content`MSBuild `<IncludeContentInPack>` özelliği varsayılan olarak olarak `true` ayarlandığından, bir paketin *içerik* klasörüne yerleştirilir.
Daha fazla bilgi için bkz. [bir paketteki Içerik ekleme](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"`, proje göreli dosya yoluna paket yolu ayarlamanın kısa bir yoludur.

## <a name="testrunner"></a>TestRunner belirtilmelidir

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

## <a name="see-also"></a>Ayrıca bkz.

- [CLı 'deki değişikliklere üst düzey genel bakış](cli-msbuild-architecture.md)
