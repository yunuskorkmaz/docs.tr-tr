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
# <a name="netsdk1080-packagereference-to-microsoftaspnetcoreapp-is-not-necessary"></a>NETSDK1080: Microsoft. AspNetCore. app için PackageReference gerekli değil

NETSDK1080, `PackageReference` proje dosyanızda için öğesinin gerekli olmadığı konusunda sizi uyarır `Microsoft.AspNetCore.App` . Tam hata iletisi aşağıdaki örneğe benzer:

> Uyarı NETSDK1080: .NET Core 3,0 veya üzeri hedeflenirken Microsoft. AspNetCore. app 'e yönelik bir PackageReference gerekli değildir. Microsoft. NET. SDK. Web kullanılıyorsa, paylaşılan çerçeveye otomatik olarak başvurulur. Aksi takdirde, PackageReference bir FrameworkReference ile değiştirilmelidir.

Bu hata genellikle bir projeyi .NET Core 3,0 veya sonraki bir sürüme yükselttikten sonra, proje dosyasında gerekli girişleri gerektiren önceki bir sürümden gerçekleştirdikten sonra oluşur `PackageReference` .

## <a name="aspnet-core-project-files"></a>Proje dosyaları ASP.NET Core

Örneğin, özgün proje dosyanız şu örnekteki gibi görünebilir:

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

.NET Core 3,1 güncelleştirildikten sonra, aynı proje için proje dosyası aşağıdaki örnekteki gibi görünmelidir:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Uyarıyı ortadan kaldırmak için bu değişiklikleri belirli bir şekilde silin `PackageReference` . Daha fazla bilgi için bkz. [Kullanımdan kaldırılmış paket başvurularını kaldır](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).

## <a name="class-library-project"></a>Sınıf kitaplığı projesi

ASP.NET Core API 'Leri kullanan bir sınıf kitaplığı projesinde, `PackageReference` `FrameworkReference` Aşağıdaki örnekte gösterildiği gibi öğesini ile değiştirin:

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

Daha fazla bilgi için bkz. [bir sınıf kitaplığında ASP.NET Core API 'Leri kullanma](/aspnet/core/fundamentals/target-aspnetcore).
