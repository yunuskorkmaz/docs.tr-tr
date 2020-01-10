---
title: .NET Core araçları 'nda bağımlılıkları yönetme
description: .NET Core araçlarıyla bağımlılıklarınızın nasıl yönetileceğini açıklar.
ms.date: 03/06/2017
ms.openlocfilehash: 9c088829ce3d5197198b7ff22a1331b8baba41d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714205"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>.NET Core SDK 1,0 ile bağımlılıkları yönetme

.NET Core projelerinin Project. json ' dan csproj ve MSBuild 'e taşınması sayesinde, proje dosyası ve bağımlılık izlemeye izin veren varlıkların birleşme ile sonuçlanan önemli bir yatırım gerçekleşsin. .NET Core projeleri için bu, Project. JSON ile benzerdir. NuGet bağımlılıklarını izleyen ayrı bir JSON veya XML dosyası yoktur. Bu değişiklik ile, `<PackageReference>`adlı csproj sözdizimine başka bir *başvuru* türü de sunuyoruz. 

Bu belgede yeni başvuru türü açıklanmaktadır. Ayrıca, bu yeni başvuru türünü kullanarak projenize nasıl bir paket bağımlılığı ekleneceğini gösterir. 

## <a name="the-new-packagereference-element"></a>Yeni \<PackageReference > öğesi
`<PackageReference>` aşağıdaki temel yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

MSBuild hakkında bilginiz varsa, zaten mevcut olan diğer başvuru türlerine tanıdık gelecektir. Anahtar, projeye eklemek istediğiniz paket kimliğini belirten `Include` deyimidir. `<Version>` Child öğesi alınacak sürümü belirtir. Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına olarak belirtilir.

> [!NOTE]
> Genel `csproj` söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.  

Yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek aşağıdaki örnekteki gibi koşullar kullanılarak yapılır:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Yukarıdaki, bağımlılık yalnızca söz konusu hedef için derleme gerçekleşince geçerli olacağı anlamına gelir. Koşuldaki `$(TargetFramework)`, projede ayarlanan MSBuild özelliğidir. En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez. 

## <a name="adding-a-dependency-to-your-project"></a>Projenize bağımlılık ekleme
Projenize bağımlılık eklemek basittir. Projenize Json.NET Version `9.0.1` eklemenin bir örneği aşağıda verilmiştir. Tabii ki, diğer herhangi bir NuGet bağımlılığı için geçerlidir. 

Proje dosyanızı açtığınızda, iki veya daha fazla `<ItemGroup>` düğümü görürsünüz. Düğümlerden birinin zaten `<PackageReference>` öğeleri olduğunu fark edeceksiniz. Yeni bağımlılığı bu düğüme ekleyebilir veya yeni bir tane oluşturabilirsiniz; Sonuç aynı olacağı için tamamen size kadar sürer. 

Bu örnekte, `dotnet new console`tarafından bırakılan varsayılan şablonu kullanacağız. Bu basit bir konsol uygulamasıdır. Projeyi açtıklarında, ilk olarak zaten var olan `<PackageReference>` `<ItemGroup>` bulduk. Daha sonra aşağıdaki öğesine ekleyin:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Bundan sonra, projeyi kaydeder ve bağımlılığı yüklemek için `dotnet restore` komutunu çalıştırırsınız. 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Tam proje şöyle görünür:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a>Bir bağımlılığı projeden kaldırma
Proje dosyasından bir bağımlılığı kaldırmak, `<PackageReference>` proje dosyasından kaldırmayı içerir.
