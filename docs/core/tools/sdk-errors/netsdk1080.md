---
title: 'NETSDK1080: Microsoft. AspNetCore. app için PackageReference gerekli değil'
description: Proje dosyanızda gereksiz bir girdi hakkında uyaran .NET SDK hatası NETSDK1080 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 02/25/2021
f1_keywords:
- NETSDK1080
ms.openlocfilehash: ebf9484e4a358597a1177f95e92f68330180cd35
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206807"
---
# <a name="netsdk1080-packagereference-to-microsoftaspnetcoreapp-is-not-necessary"></a><span data-ttu-id="51d41-103">NETSDK1080: Microsoft. AspNetCore. app için PackageReference gerekli değil</span><span class="sxs-lookup"><span data-stu-id="51d41-103">NETSDK1080: PackageReference to Microsoft.AspNetCore.App is not necessary</span></span>

<span data-ttu-id="51d41-104">NETSDK1080, `PackageReference` proje dosyanızda için öğesinin gerekli olmadığı konusunda sizi uyarır `Microsoft.AspNetCore.App` .</span><span class="sxs-lookup"><span data-stu-id="51d41-104">NETSDK1080 warns you that the `PackageReference` element for `Microsoft.AspNetCore.App` in your project file is not necessary.</span></span> <span data-ttu-id="51d41-105">Tam hata iletisi aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="51d41-105">The full error message is similar to the following example:</span></span>

> <span data-ttu-id="51d41-106">Uyarı NETSDK1080: .NET Core 3,0 veya üzeri hedeflenirken Microsoft. AspNetCore. app 'e yönelik bir PackageReference gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="51d41-106">warning NETSDK1080: A PackageReference to Microsoft.AspNetCore.App is not necessary when targeting .NET Core 3.0 or higher.</span></span> <span data-ttu-id="51d41-107">Microsoft. NET. SDK. Web kullanılıyorsa, paylaşılan çerçeveye otomatik olarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="51d41-107">If Microsoft.NET.Sdk.Web is used, the shared framework will be referenced automatically.</span></span> <span data-ttu-id="51d41-108">Aksi takdirde, PackageReference bir FrameworkReference ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="51d41-108">Otherwise, the PackageReference should be replaced with a FrameworkReference.</span></span>

<span data-ttu-id="51d41-109">Bu hata genellikle bir projeyi .NET Core 3,0 veya sonraki bir sürüme yükselttikten sonra, proje dosyasında gerekli girişleri gerektiren önceki bir sürümden gerçekleştirdikten sonra oluşur `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="51d41-109">This error typically occurs after you've upgraded a project to .NET Core 3.0 or later, from an earlier version that required `PackageReference` entries in the project file.</span></span>

## <a name="aspnet-core-project-files"></a><span data-ttu-id="51d41-110">Proje dosyaları ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51d41-110">ASP.NET Core project files</span></span>

<span data-ttu-id="51d41-111">Örneğin, özgün proje dosyanız şu örnekteki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="51d41-111">For example, your original project file might look like this example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp2.2</TargetFramework>
    <AspNetCoreHostingModel>InProcess</AspNetCoreHostingModel>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.App"/>
    <PackageReference Include="Microsoft.AspNetCore.Razor.Design" Version="2.2.0" PrivateAssets="All" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="51d41-112">.NET Core 3,1 güncelleştirildikten sonra, aynı proje için proje dosyası aşağıdaki örnekteki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="51d41-112">After updating to .NET Core 3.1 the project file for the same project should look like the following example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="51d41-113">Uyarıyı ortadan kaldırmak için bu değişiklikleri belirli bir şekilde silin `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="51d41-113">Make these changes, in particular delete the `PackageReference` element, to eliminate the warning.</span></span> <span data-ttu-id="51d41-114">Daha fazla bilgi için bkz. [Kullanımdan kaldırılmış paket başvurularını kaldır](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).</span><span class="sxs-lookup"><span data-stu-id="51d41-114">For more information, see [Remove obsolete package references](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).</span></span>

## <a name="class-library-project"></a><span data-ttu-id="51d41-115">Sınıf kitaplığı projesi</span><span class="sxs-lookup"><span data-stu-id="51d41-115">Class library project</span></span>

<span data-ttu-id="51d41-116">ASP.NET Core API 'Leri kullanan bir sınıf kitaplığı projesinde, `PackageReference` `FrameworkReference` Aşağıdaki örnekte gösterildiği gibi öğesini ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="51d41-116">In a class library project that uses ASP.NET Core APIs, replace the `PackageReference` with a `FrameworkReference`, as shown in the following example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <FrameworkReference Include="Microsoft.AspNetCore.App" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="51d41-117">Daha fazla bilgi için bkz. [bir sınıf kitaplığında ASP.NET Core API 'Leri kullanma](/aspnet/core/fundamentals/target-aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="51d41-117">For more information, see [Use ASP.NET Core APIs in a class library](/aspnet/core/fundamentals/target-aspnetcore).</span></span>
