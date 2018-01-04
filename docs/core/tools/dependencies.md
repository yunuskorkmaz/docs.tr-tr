---
title: ".NET Core araç bağımlılıkları yönetme"
description: "Bağımlılıklarınız .NET Core araçları ile yönetmek açıklanmaktadır."
keywords: "CLI, genişletilebilirlik, özel komutlar, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.workload: dotnetcore
ms.openlocfilehash: a064ae72a077583cfb544309700555ebd9d398a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Bağımlılıkları .NET Core SDK 1.0 ile yönetme

Önemli bir yatırımın, taşımak .NET Core projeleri ile project.json csproj ve MSBuild, proje dosyası ve bağımlılıkları izleme izin varlıklar Birleştirici içinde sonuçlanan ayrıca oluştu. .NET Core projelerde bu hangi project.json vermedi için benzer. NuGet bağımlılıkları izleyen ayrı JSON veya XML dosya yok. Bu değişiklikle, biz de başka bir tür ekledik *başvuru* adlı csproj sözdizimi içine `<PackageReference>`. 

Bu belgede yeni başvuru türü açıklanmaktadır. Ayrıca, bu yeni başvuru türü projenize kullanarak bir paket bağımlılığı eklemek nasıl gösterir. 

## <a name="the-new-packagereference-element"></a>Yeni \<PackageReference > öğesi
`<PackageReference>` Aşağıdaki temel yapı vardır:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

MSBuild ile hakkında bilginiz varsa, zaten bulunan diğer başvuru türleri için tanıdık gelecektir. Anahtar `Include` deyimi projeye eklemek istediğiniz paket kimliğini belirtir. `<Version>` Alt öğesi almak için sürümünü belirtir. Sürümleri göre belirtilen [NuGet sürümü kurallarını](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Bütün ile bilmiyorsanız `csproj` sözdizimi, bkz: [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) daha fazla bilgi için.  

Yalnızca belirli bir hedef olarak kullanılabilir bir bağımlılık ekleme gerçekleştirilir gibi koşullar aşağıdaki örnekte kullanarak:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

Bağımlılık yalnızca derleme için hedef verilen oluşuyorsa geçerli olacağını yukarıdaki anlamına gelir. `$(TargetFramework)` Koşulunda projede ayarlandığında bir MSBuild özelliğidir. En yaygın .NET Core uygulamalar için bunu yapmak gerekmez. 

## <a name="adding-a-dependency-to-your-project"></a>Projenize bir bağımlılık ekleme
Projenize bir bağımlılık ekleme basittir. Json.NET sürüm ekleme konusunda bir örneği burada verilmiştir `9.0.1` projenize. Elbette, herhangi bir NuGet bağımlılığı için geçerlidir. 

Proje dosyası açtığınızda, iki veya daha fazla görürsünüz `<ItemGroup>` düğümleri. Düğümlerden birinde zaten olduğunu fark edeceksiniz `<PackageReference>` öğelere. Bu düğüm, yeni bağımlılık ekleme ya da yeni bir tane oluşturun; Sonuç aynı olacak şekilde, tamamen size bağlıdır. 

Bu örnekte bırakılan tarafından varsayılan şablonu kullanacağız `dotnet new console`. Basit bir konsol uygulaması budur. Biz projeyi açtığınızda, biz ilk Bul `<ItemGroup>` zaten var olan `<PackageReference>` da. Biz ardından aşağıdakileri ekleyin:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Bundan sonra biz projeyi kaydedin ve Çalıştır `dotnet restore` bağımlılık yüklemek için komutu. 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Tam proje şöyle görünür:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a>Bir bağımlılık projeden kaldırma
Proje dosyasından bir bağımlılık kaldırmayı içerir yalnızca kaldırma `<PackageReference>` proje dosyasından.
