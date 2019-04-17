---
title: .NET Core araçları bağımlılıkları yönetme
description: .NET Core araçları ile bağımlılıklarınızı yönetmesini açıklanmaktadır.
ms.date: 03/06/2017
ms.custom: seodec18
ms.openlocfilehash: ef2de666ee3e6a06ab62f45afe3c624bbbb44ac4
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611933"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>.NET Core SDK'sı 1.0 ile bağımlılık Yönetimi

Ciddi bir yatırım, taşıma, .NET Core projeleri ile project.json'ndan csproj ve MSBuild proje dosyası ve bağımlılıkları izlenmesine izin vermek varlıklar birleştirmesi içinde sonuçlanan da oldu. .NET Core projeleri için hangi project.json benzer budur. NuGet bağımlılıklarını izleyen ayrı JSON veya XML dosya yok. Bu değişiklik, aynı zamanda başka bir tür tanıttık *başvuru* adlı csproj söz dizimini içine `<PackageReference>`. 

Bu belge, yeni başvuru türünü açıklar. Ayrıca bu yeni bir başvuru türü projenize kullanarak paket bağımlılık ekleme işlemini de gösterir. 

## <a name="the-new-packagereference-element"></a>Yeni \<PackageReference > öğesi
`<PackageReference>` Aşağıdaki temel yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Msbuild'i iyi bilmiyorsanız, zaten mevcut olan diğer başvuru türlerine benzer görünecektir. Anahtar `Include` deyimi projeye eklemek istediğiniz paket kimliğini belirtir. `<Version>` Sürümü almak için alt öğe belirtir. Sürümler olarak başına belirtilen [NuGet sürümü kurallarını](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Genel ile aşina değilseniz `csproj` söz dizimini bkz [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) daha fazla bilgi için belgelere bakın.  

Yalnızca belirli bir hedef olarak kullanılabilir bir bağımlılık ekleme yapılır gibi koşullar kullanarak aşağıdaki örnekte:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Bağımlılık yalnızca derleme için hedef verilen karşılaşıyorsanız geçerli olacağını yukarıdaki anlamına gelir. `$(TargetFramework)` Koşulda projede ayarlanan bir MSBuild özelliğidir. En yaygın .NET Core uygulamaları için bunu yapmak gerekmez. 

## <a name="adding-a-dependency-to-your-project"></a>Projenize bir bağımlılık ekleme
Bir bağımlılık projenize eklemek oldukça basittir. İşte bir örnek Json.NET sürüm ekleme `9.0.1` projenize. Elbette, diğer NuGet bağımlılık için geçerlidir. 

Proje dosyanız açtığınızda, iki veya daha fazla görürsünüz `<ItemGroup>` düğümleri. Düğümlerden biri zaten olduğunu fark edebilirsiniz `<PackageReference>` öğelere. Bu düğüme yeni, bağımlılık ekleme ya da yeni bir tane oluşturun; Sonuç aynı olacaktır. Bu tamamen size bağlıdır aynıdır. 

Bu örnekte bırakılan tarafından varsayılan şablonu kullanacağız `dotnet new console`. Bu basit bir konsol uygulamasıdır. Biz projeyi açtığınızda, ilk buluyoruz `<ItemGroup>` zaten varolan `<PackageReference>` da. Biz ardından aşağıdakileri ekleyin:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Bundan sonra biz projeyi kaydedin ve çalıştırın `dotnet restore` bağımlılık yüklemek için komutu. 

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

## <a name="removing-a-dependency-from-the-project"></a>Projeden bir bağımlılık kaldırma
Proje dosyasından bir bağımlılık kaldırmayı içerir yalnızca kaldırma `<PackageReference>` proje dosyasında.
