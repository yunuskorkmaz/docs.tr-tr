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
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="158d6-104">Project.json ve csproj özellikleri arasında bir eşleme</span><span class="sxs-lookup"><span data-stu-id="158d6-104">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="158d6-105">Tarafından [Can Etikan McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="158d6-105">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="158d6-106">.NET Core araç geliştirme sırasında artık desteklemek için bir önemli tasarım değişikliğin yapıldığı *project.json* dosyaları ve bunun yerine .NET Core projeleri MSBuild/csproj biçimine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="158d6-106">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="158d6-107">Bu makalede gösterilmektedir nasıl ayarlarında *project.json* yeni biçimini kullanın ve projenize yükseltirken geçiş araçları tarafından yapılan değişiklikleri anlama hakkında bilgi için MSBuild/csproj biçiminde gösterilir araç en son sürümü.</span><span class="sxs-lookup"><span data-stu-id="158d6-107">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span> 
 
## <a name="the-csproj-format"></a><span data-ttu-id="158d6-108">Csproj biçimi</span><span class="sxs-lookup"><span data-stu-id="158d6-108">The csproj format</span></span>

<span data-ttu-id="158d6-109">Yeni biçim \*.csproj, XML tabanlı bir biçim değil.</span><span class="sxs-lookup"><span data-stu-id="158d6-109">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="158d6-110">Aşağıdaki örnek, .NET Core kullanarak proje kök düğümü gösterir `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="158d6-110">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="158d6-111">Web projeleri için kullanılan SDK olduğu `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="158d6-111">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="158d6-112">Ortak üst düzey özellikleri</span><span class="sxs-lookup"><span data-stu-id="158d6-112">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="158d6-113">name</span><span class="sxs-lookup"><span data-stu-id="158d6-113">name</span></span>
```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="158d6-114">Artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="158d6-114">No longer supported.</span></span> <span data-ttu-id="158d6-115">Csproj içinde bu dizin adıyla tanımlanan proje filename tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="158d6-115">In csproj, this is determined by the project filename, which is defined by the directory name.</span></span> <span data-ttu-id="158d6-116">Örneğin, `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="158d6-116">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="158d6-117">Varsayılan olarak, proje filename de değerini belirtir. `<AssemblyName>` ve `<PackageId>` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="158d6-117">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span> 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="158d6-118">`<AssemblyName>` Farklı bir değere sahip olur `<PackageId>` varsa `buildOptions\outputName` özelliği, project.json tanımlanmıştı.</span><span class="sxs-lookup"><span data-stu-id="158d6-118">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span> <span data-ttu-id="158d6-119">Daha fazla bilgi için bkz: [başka bir genel derleme seçenekleri](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="158d6-119">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="158d6-120">sürüm</span><span class="sxs-lookup"><span data-stu-id="158d6-120">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```
<span data-ttu-id="158d6-121">Kullanım `VersionPrefix` ve `VersionSuffix` özellikleri:</span><span class="sxs-lookup"><span data-stu-id="158d6-121">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="158d6-122">Aynı zamanda `Version` özelliği, ancak bu ayarları geçersiz kılar sürüm paketlemesi sırasında:</span><span class="sxs-lookup"><span data-stu-id="158d6-122">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="158d6-123">Diğer ortak kök düzeyinde seçenekleri</span><span class="sxs-lookup"><span data-stu-id="158d6-123">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="158d6-124">çerçeveler</span><span class="sxs-lookup"><span data-stu-id="158d6-124">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="158d6-125">Bir hedef framework</span><span class="sxs-lookup"><span data-stu-id="158d6-125">One target framework</span></span>
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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="158d6-126">Birden çok hedef çerçeveyi</span><span class="sxs-lookup"><span data-stu-id="158d6-126">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="158d6-127">Kullanım `TargetFrameworks` hedef çerçeveyi listesini tanımlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="158d6-127">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="158d6-128">Birden çok framework değerleri ayırmak için noktalı virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="158d6-128">Use semi-colon to separate multiple framework values.</span></span> 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="158d6-129">bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="158d6-129">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="158d6-130">Bağımlılık ise bir **proje** ve bir paket biçimi farklıdır.</span><span class="sxs-lookup"><span data-stu-id="158d6-130">If the dependency is a **project** and not a package, the format is different.</span></span> <span data-ttu-id="158d6-131">Daha fazla bilgi için bkz: [bağımlılık türü](#dependency-type) bölümü.</span><span class="sxs-lookup"><span data-stu-id="158d6-131">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="158d6-132">NETStandard.Library metapackage</span><span class="sxs-lookup"><span data-stu-id="158d6-132">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="158d6-133">Microsoft.NETCore.App metapackage</span><span class="sxs-lookup"><span data-stu-id="158d6-133">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="158d6-134">Unutmayın `<RuntimeFrameworkVersion>` değeri geçirilen projesinde yüklü olan SDK sürümü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="158d6-134">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="158d6-135">Üst düzey bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="158d6-135">Top-level dependencies</span></span>
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

### <a name="per-framework-dependencies"></a><span data-ttu-id="158d6-136">Çerçeve başına bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="158d6-136">Per-framework dependencies</span></span>
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

### <a name="imports"></a><span data-ttu-id="158d6-137">içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="158d6-137">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="158d6-138">Bağımlılık türü</span><span class="sxs-lookup"><span data-stu-id="158d6-138">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="158d6-139">Tür: Proje</span><span class="sxs-lookup"><span data-stu-id="158d6-139">type: project</span></span>
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
> <span data-ttu-id="158d6-140">Bu şekilde kesilir, `dotnet pack --version-suffix $suffix` proje başvurusu bağımlılık sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="158d6-140">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>


#### <a name="type-build"></a><span data-ttu-id="158d6-141">Tür: derleme</span><span class="sxs-lookup"><span data-stu-id="158d6-141">type: build</span></span>
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

#### <a name="type-platform"></a><span data-ttu-id="158d6-142">Tür: platform</span><span class="sxs-lookup"><span data-stu-id="158d6-142">type: platform</span></span>
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

<span data-ttu-id="158d6-143">İçinde csproj eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="158d6-143">There is no equivalent in csproj.</span></span> 

## <a name="runtimes"></a><span data-ttu-id="158d6-144">Çalışma zamanları</span><span class="sxs-lookup"><span data-stu-id="158d6-144">runtimes</span></span>
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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="158d6-145">Tek başına uygulamaları (kendi içinde bulunan bir dağıtım)</span><span class="sxs-lookup"><span data-stu-id="158d6-145">Standalone apps (self-contained deployment)</span></span>
<span data-ttu-id="158d6-146">Project.JSON tanımlayan bir `runtimes` uygulama edildi sırasında tek başına bölüm anlamına gelir oluşturma ve yayımlama.</span><span class="sxs-lookup"><span data-stu-id="158d6-146">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="158d6-147">MSBuild tüm projeleri olan *taşınabilir* derleme, ancak tek başına olarak yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="158d6-147">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="158d6-148">Daha fazla bilgi için bkz: [müstakil dağıtımları (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="158d6-148">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span>

## <a name="tools"></a><span data-ttu-id="158d6-149">araçlar</span><span class="sxs-lookup"><span data-stu-id="158d6-149">tools</span></span>
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
> <span data-ttu-id="158d6-150">`imports`Araçlar ' csproj desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="158d6-150">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="158d6-151">İçeri aktarmalar gereken araçları yeni çalışmaz `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="158d6-151">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="158d6-152">buildOptions</span><span class="sxs-lookup"><span data-stu-id="158d6-152">buildOptions</span></span>

<span data-ttu-id="158d6-153">Ayrıca bkz. [dosyaları](#files).</span><span class="sxs-lookup"><span data-stu-id="158d6-153">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="158d6-154">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="158d6-154">emitEntryPoint</span></span>

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

<span data-ttu-id="158d6-155">Varsa `emitEntryPoint` olan `false`, değeri `OutputType` dönüştürülür `Library`, varsayılan değer olan:</span><span class="sxs-lookup"><span data-stu-id="158d6-155">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="158d6-156">keyFile</span><span class="sxs-lookup"><span data-stu-id="158d6-156">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="158d6-157">`keyFile` Öğesi genişletir MSBuild üç özelliklerinde için:</span><span class="sxs-lookup"><span data-stu-id="158d6-157">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="158d6-158">Diğer ortak derleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="158d6-158">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="158d6-159">packOptions</span><span class="sxs-lookup"><span data-stu-id="158d6-159">packOptions</span></span>

<span data-ttu-id="158d6-160">Ayrıca bkz. [dosyaları](#files).</span><span class="sxs-lookup"><span data-stu-id="158d6-160">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="158d6-161">Ortak paketi seçenekleri</span><span class="sxs-lookup"><span data-stu-id="158d6-161">Common pack options</span></span>

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

<span data-ttu-id="158d6-162">İçin bir eşdeğeri yoktur `owners` MSBuild öğesinde.</span><span class="sxs-lookup"><span data-stu-id="158d6-162">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="158d6-163">İçin `summary`, MSBuild kullanabilirsiniz `<Description>` özelliği, olsa bile değerini `summary` bu özelliği bu yana otomatik olarak bu özelliğe geçirilmez [ `description` ](#-other-common-root-level-options) öğesi.</span><span class="sxs-lookup"><span data-stu-id="158d6-163">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#-other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="158d6-164">betikler</span><span class="sxs-lookup"><span data-stu-id="158d6-164">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="158d6-165">Kendi eşdeğerdir msbuild'de [hedefleri](/visualstudio/msbuild/msbuild-targets):</span><span class="sxs-lookup"><span data-stu-id="158d6-165">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```


## <a name="runtimeoptions"></a><span data-ttu-id="158d6-166">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="158d6-166">runtimeOptions</span></span>

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

<span data-ttu-id="158d6-167">Bu gruptaki "System.GC.Server" özellik dışında tüm ayarlar adlı bir dosyaya yerleştirilir *runtimeconfig.template.json* proje klasöründeki kök nesnesine geçiş işlemi sırasında kaldırılmış seçeneklerle:</span><span class="sxs-lookup"><span data-stu-id="158d6-167">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="158d6-168">"System.GC.Server" özelliği csproj dosyasına geçirilir:</span><span class="sxs-lookup"><span data-stu-id="158d6-168">The "System.GC.Server" property is migrated into the csproj file:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="158d6-169">Ancak, bu değerleri csproj yanı sıra MSBuild özellikleri ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="158d6-169">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="158d6-170">shared</span><span class="sxs-lookup"><span data-stu-id="158d6-170">shared</span></span>
```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="158d6-171">Csproj içinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="158d6-171">Not supported in csproj.</span></span> <span data-ttu-id="158d6-172">Bunun yerine oluşturmalısınız içerik dosyalarına eklemek, *.nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="158d6-172">You must instead create include content files in your *.nuspec* file.</span></span> <span data-ttu-id="158d6-173">Daha fazla bilgi için bkz: [içerik dosyaları dahil olmak üzere](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="158d6-173">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="158d6-174">dosyaları</span><span class="sxs-lookup"><span data-stu-id="158d6-174">files</span></span>

<span data-ttu-id="158d6-175">İçinde *project.json*, yapı ve paketi genişletilmiş derlemek ve farklı klasörlerden katıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="158d6-175">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="158d6-176">MSBuild içinde bu yapılır kullanarak [öğeleri](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="158d6-176">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="158d6-177">Aşağıdaki örnek, ortak bir dönüştürme verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="158d6-177">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="158d6-178">Varsayılan birçok [genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) .NET Core SDK'sı tarafından otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="158d6-178">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="158d6-179">Daha fazla bilgi için bkz: [varsayılan derleme öğesi değerleri](https://aka.ms/sdkimplicititems).</span><span class="sxs-lookup"><span data-stu-id="158d6-179">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="158d6-180">Tüm MSBuild `ItemGroup` öğeleri Destek `Include`, `Exclude`, ve `Remove`.</span><span class="sxs-lookup"><span data-stu-id="158d6-180">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="158d6-181">Paket düzeni .nupkg içinde ile değiştirilebilir `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="158d6-181">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="158d6-182">Dışında `Content`, çoğu öğesi gruplarını açıkça ekleme gerektiren `Pack="true"` pakete dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="158d6-182">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="158d6-183">`Content`işaretleneceğini belirtilir *içerik* MSBuild itibaren bir paket klasörüne `<IncludeContentInPack>` özelliği ayarlanmış `true` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="158d6-183">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span> <span data-ttu-id="158d6-184">Daha fazla bilgi için bkz: [bir paketteki içerik dahil olmak üzere](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="158d6-184">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="158d6-185">`PackagePath="%(Identity)"`Proje göreli dosya yolu paket yolu ayarlama kısa bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="158d6-185">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="158d6-186">testRunner</span><span class="sxs-lookup"><span data-stu-id="158d6-186">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="158d6-187">xUnit</span><span class="sxs-lookup"><span data-stu-id="158d6-187">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="158d6-188">MSTest</span><span class="sxs-lookup"><span data-stu-id="158d6-188">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="158d6-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="158d6-189">See Also</span></span>

[<span data-ttu-id="158d6-190">CLI değişiklikleri üst düzey genel bakış</span><span class="sxs-lookup"><span data-stu-id="158d6-190">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
