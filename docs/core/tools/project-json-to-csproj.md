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
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="0df33-103">project.json ve csproj özellikleri arasında bir haritalama</span><span class="sxs-lookup"><span data-stu-id="0df33-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="0df33-104">Yazar: [Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="0df33-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="0df33-105">.NET Core takımlamanın geliştirilmesi sırasında, *project.json* dosyalarını artık desteklememek ve bunun yerine .NET Core projelerini MSBuild/csproj biçimine taşımak için önemli bir tasarım değişikliği yapıldı.</span><span class="sxs-lookup"><span data-stu-id="0df33-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="0df33-106">Bu makalede, *project.json'daki* ayarların MSBuild/csproj formatında nasıl temsil edildiği gösterilmektedir, böylece yeni biçimi nasıl kullanacağınızı öğrenebilir ve projenizi araçlamanın en son sürümüne yükseltirken geçiş araçları tarafından yapılan değişiklikleri anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0df33-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="0df33-107">Csproj formatı</span><span class="sxs-lookup"><span data-stu-id="0df33-107">The csproj format</span></span>

<span data-ttu-id="0df33-108">Yeni biçim, \*.csproj, XML tabanlı bir biçimdir.</span><span class="sxs-lookup"><span data-stu-id="0df33-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="0df33-109">Aşağıdaki örnekte .NET Core projesinin kök düğümünü kullanarak `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="0df33-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="0df33-110">Web projeleri için Kullanılan SDK' dır. `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="0df33-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="0df33-111">Ortak üst düzey özellikler</span><span class="sxs-lookup"><span data-stu-id="0df33-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="0df33-112">ad</span><span class="sxs-lookup"><span data-stu-id="0df33-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="0df33-113">Artık desteklenmiå.</span><span class="sxs-lookup"><span data-stu-id="0df33-113">No longer supported.</span></span> <span data-ttu-id="0df33-114">Csproj'da bu, genellikle dizin adı ile eşleşen proje dosya adı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0df33-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="0df33-115">Örneğin, `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="0df33-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="0df33-116">Varsayılan olarak, proje dosya adı da ve `<AssemblyName>` `<PackageId>` özelliklerideğerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0df33-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="0df33-117">Özellik `<AssemblyName>` project.json'da `buildOptions\outputName` tanımlanmışsa, `<PackageId>` farklı bir değere sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0df33-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="0df33-118">Daha fazla bilgi için [bkz.](#other-common-build-options)</span><span class="sxs-lookup"><span data-stu-id="0df33-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="0df33-119">version</span><span class="sxs-lookup"><span data-stu-id="0df33-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="0df33-120">Kullanım `VersionPrefix` ve `VersionSuffix` özellikleri:</span><span class="sxs-lookup"><span data-stu-id="0df33-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="0df33-121">`Version` Özelliği de kullanabilirsiniz, ancak bu, paketleme sırasında sürüm ayarlarını geçersiz kılabilir:</span><span class="sxs-lookup"><span data-stu-id="0df33-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="0df33-122">Diğer ortak kök düzeyi seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0df33-122">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="0df33-123">Çerçeve</span><span class="sxs-lookup"><span data-stu-id="0df33-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="0df33-124">Tek hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="0df33-124">One target framework</span></span>

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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="0df33-125">Birden çok hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="0df33-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="0df33-126">Hedef `TargetFrameworks` çerçeveler listenizi tanımlamak için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="0df33-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="0df33-127">Birden çok çerçeve değerlerini ayırmak için yarı iki nokta üst üste kullanın.</span><span class="sxs-lookup"><span data-stu-id="0df33-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="0df33-128">bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0df33-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0df33-129">Bağımlılık bir paket değil, bir **projeyse,** biçim farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0df33-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="0df33-130">Daha fazla bilgi için [bağımlılık türü](#dependency-type) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0df33-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="0df33-131">NETStandard.Library metapaketi</span><span class="sxs-lookup"><span data-stu-id="0df33-131">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="0df33-132">Microsoft.NETCore.App metapaketi</span><span class="sxs-lookup"><span data-stu-id="0df33-132">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="0df33-133">Geçirilen projedeki değerin `<RuntimeFrameworkVersion>` yüklediğiniz SDK sürümütarafından belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0df33-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="0df33-134">Üst düzey bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0df33-134">Top-level dependencies</span></span>

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

### <a name="per-framework-dependencies"></a><span data-ttu-id="0df33-135">Çerçeve başına bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0df33-135">Per-framework dependencies</span></span>

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

### <a name="imports"></a><span data-ttu-id="0df33-136">içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="0df33-136">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="0df33-137">bağımlılık türü</span><span class="sxs-lookup"><span data-stu-id="0df33-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="0df33-138">türü: proje</span><span class="sxs-lookup"><span data-stu-id="0df33-138">type: project</span></span>

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
> <span data-ttu-id="0df33-139">Bu, proje başvurusu `dotnet pack --version-suffix $suffix` bağımlılık sürümünü belirleyen yolu kıracak.</span><span class="sxs-lookup"><span data-stu-id="0df33-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="0df33-140">türü: yapı</span><span class="sxs-lookup"><span data-stu-id="0df33-140">type: build</span></span>

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

#### <a name="type-platform"></a><span data-ttu-id="0df33-141">türü: platform</span><span class="sxs-lookup"><span data-stu-id="0df33-141">type: platform</span></span>

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

<span data-ttu-id="0df33-142">Csproj'da eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="0df33-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="0df33-143">Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0df33-143">runtimes</span></span>

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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="0df33-144">Bağımsız uygulamalar (bağımsız dağıtım)</span><span class="sxs-lookup"><span data-stu-id="0df33-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="0df33-145">Project.json'da, bir `runtimes` bölümü tanımlamak, uygulamanın yapı ve yayımlama sırasında tek başına olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0df33-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="0df33-146">MSBuild'te, tüm projeler yapı sırasında *taşınabilirdir,* ancak bağımsız olarak yayınlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0df33-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="0df33-147">Daha fazla bilgi için [bkz.](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="0df33-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="0df33-148">araçlar</span><span class="sxs-lookup"><span data-stu-id="0df33-148">tools</span></span>

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
> <span data-ttu-id="0df33-149">`imports`araçlar da csproj desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0df33-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="0df33-150">İthalat gerektiren araçlar yeni `Microsoft.NET.Sdk`ile çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="0df33-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="0df33-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="0df33-151">buildOptions</span></span>

<span data-ttu-id="0df33-152">Ayrıca [Bakınız Dosyalar](#files).</span><span class="sxs-lookup"><span data-stu-id="0df33-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="0df33-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="0df33-153">emitEntryPoint</span></span>

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

<span data-ttu-id="0df33-154">Ise `emitEntryPoint` `false`, değeri `OutputType` varsayılan değer `Library`olan , dönüştürülür:</span><span class="sxs-lookup"><span data-stu-id="0df33-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="0df33-155">Keyfile</span><span class="sxs-lookup"><span data-stu-id="0df33-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="0df33-156">Öğe `keyFile` MSBuild üç özelliklere genişletir:</span><span class="sxs-lookup"><span data-stu-id="0df33-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="0df33-157">Diğer ortak yapı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0df33-157">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="0df33-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="0df33-158">packOptions</span></span>

<span data-ttu-id="0df33-159">Ayrıca [Bakınız Dosyalar](#files).</span><span class="sxs-lookup"><span data-stu-id="0df33-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="0df33-160">Ortak paket seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0df33-160">Common pack options</span></span>

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

<span data-ttu-id="0df33-161">MSBuild'teki öğenin eşdeğeri `owners` yoktur.</span><span class="sxs-lookup"><span data-stu-id="0df33-161">There is no equivalent for the `owners` element in MSBuild.</span></span>
<span data-ttu-id="0df33-162">Çünkü, `summary`değeri `<Description>` `summary` bu özelliğe otomatik olarak geçirilemese de, bu özellik [`description`](#other-common-root-level-options) öğeye eşlenmiş olduğundan, MSBuild özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0df33-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="0df33-163">betikler</span><span class="sxs-lookup"><span data-stu-id="0df33-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="0df33-164">MSBuild onların eşdeğer [hedefleri](/visualstudio/msbuild/msbuild-targets)şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0df33-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="0df33-165">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="0df33-165">runtimeOptions</span></span>

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

<span data-ttu-id="0df33-166">"System.GC.Server" özelliği dışında bu gruptaki tüm ayarlar, proje klasöründe *runtimeconfig.template.json* adlı bir dosyaya yerleştirilir ve geçiş işlemi sırasında seçenekler kök nesneye kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="0df33-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="0df33-167">"System.GC.Server" özelliği csproj dosyasına taşınır:</span><span class="sxs-lookup"><span data-stu-id="0df33-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="0df33-168">Ancak, csproj yanı sıra MSBuild özellikleri tüm bu değerleri ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0df33-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="0df33-169">shared</span><span class="sxs-lookup"><span data-stu-id="0df33-169">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="0df33-170">Csproj desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0df33-170">Not supported in csproj.</span></span> <span data-ttu-id="0df33-171">Bunun yerine *.nuspec* dosyanıza içerik dosyaları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0df33-171">You must instead create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="0df33-172">Daha fazla bilgi için [bkz.](/nuget/schema/nuspec#including-content-files)</span><span class="sxs-lookup"><span data-stu-id="0df33-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="0df33-173">files</span><span class="sxs-lookup"><span data-stu-id="0df33-173">files</span></span>

<span data-ttu-id="0df33-174">*Project.json,* build ve pack farklı klasörlerden derlemek ve katıştırmak için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="0df33-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="0df33-175">MSBuild'te bu öğeler [kullanılarak](/visualstudio/msbuild/common-msbuild-project-items)yapılır.</span><span class="sxs-lookup"><span data-stu-id="0df33-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="0df33-176">Aşağıdaki örnek, yaygın bir dönüşümdür:</span><span class="sxs-lookup"><span data-stu-id="0df33-176">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="0df33-177">Varsayılan [globbing desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) çoğu otomatik olarak .NET Core SDK tarafından eklenir.</span><span class="sxs-lookup"><span data-stu-id="0df33-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="0df33-178">Daha fazla bilgi için [bkz.](https://aka.ms/sdkimplicititems)</span><span class="sxs-lookup"><span data-stu-id="0df33-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="0df33-179">`ItemGroup` Tüm MSBuild `Include`elemanları `Exclude`destek `Remove`, ve .</span><span class="sxs-lookup"><span data-stu-id="0df33-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="0df33-180">.nupkg içindeki paket düzeni `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="0df33-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="0df33-181">Bunun `Content`dışında, çoğu öğe grubu `Pack="true"` pakete eklenmesi için açıkça eklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0df33-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="0df33-182">`Content`MSBuild `<IncludeContentInPack>` özelliği varsayılan olarak ayarlı `true` *olduğundan,* bir paketteki içerik klasörüne konulacaktır.</span><span class="sxs-lookup"><span data-stu-id="0df33-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="0df33-183">Daha fazla bilgi için [bkz.](/nuget/schema/msbuild-targets#including-content-in-a-package)</span><span class="sxs-lookup"><span data-stu-id="0df33-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="0df33-184">`PackagePath="%(Identity)"`proje ile ilgili dosya yoluna paket yolu ayarlamanın kısa bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="0df33-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="0df33-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="0df33-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="0df33-186">xBirim</span><span class="sxs-lookup"><span data-stu-id="0df33-186">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="0df33-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="0df33-187">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0df33-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0df33-188">See also</span></span>

- [<span data-ttu-id="0df33-189">CLI'deki değişikliklere üst düzey genel bakış</span><span class="sxs-lookup"><span data-stu-id="0df33-189">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
