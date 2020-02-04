---
title: .NET Core araçları 'nda bağımlılıkları yönetme
description: .NET Core araçlarıyla bağımlılıklarınızın nasıl yönetileceğini açıklar.
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965626"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>.NET Core SDK 1,0 ile bağımlılıkları yönetme

.NET Core projelerinin Project. json ' dan csproj ve MSBuild 'e taşınması sayesinde, proje dosyası ve bağımlılık izlemeye izin veren varlıkların birleşme ile sonuçlanan önemli bir yatırım gerçekleşsin. .NET Core projeleri için bu, Project. JSON öğesine benzerdir. NuGet bağımlılıklarını izleyen ayrı bir JSON veya XML dosyası yoktur. Bu değişiklik ile, `<PackageReference>`adlı csproj sözdizimine başka bir *başvuru* türü de sunuyoruz.

Bu belgede yeni başvuru türü açıklanmaktadır. Ayrıca, bu yeni başvuru türünü kullanarak projenize nasıl bir paket bağımlılığı ekleneceğini gösterir.

## <a name="the-new-packagereference-element"></a>Yeni \<PackageReference > öğesi

`<PackageReference>` aşağıdaki temel yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

MSBuild hakkında bilginiz varsa, zaten mevcut olan diğer başvuru türlerine tanıdık gelecektir. Bu anahtar, projeye eklemek istediğiniz paket KIMLIĞINI belirten `Include` deyimidir. `<Version>` Child öğesi alınacak sürümü belirtir. Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına olarak belirtilir.

> [!NOTE]
> Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.

Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Bağımlılık yalnızca, söz konusu hedef için derleme gerçekleşuyorsa geçerli olur. Koşuldaki `$(TargetFramework)`, projede ayarlanmış bir MSBuild özelliğidir. En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.

## <a name="add-a-dependency-to-the-project"></a>Projeye bağımlılık ekleme

Projenize bağımlılık eklemek basittir. Projenize Json.NET Version `9.0.1` eklemenin bir örneği aşağıda verilmiştir. Tabii ki, diğer herhangi bir NuGet bağımlılığı için geçerlidir.

Proje dosyanızda iki veya daha fazla `<ItemGroup>` düğümü vardır. Düğümlerden biri zaten içinde `<PackageReference>` öğe içeriyor. Yeni bağımlılığı bu düğüme ekleyebilir veya yeni bir tane oluşturabilirsiniz; Sonuç aynı olacaktır.

Aşağıdaki örnek, `dotnet new console`tarafından bırakılan varsayılan şablonu kullanır. Bu basit bir konsol uygulamasıdır. Projeyi açtığınızda, içinde zaten var olan `<PackageReference>` `<ItemGroup>` bulacaksınız. Aşağıdaki öğesine ekleyin:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Bundan sonra, projeyi kaydedin ve bağımlılığı yüklemek için `dotnet restore` komutunu çalıştırın.

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

## <a name="remove-a-dependency-from-the-project"></a>Bir bağımlılığı projeden kaldırma

Proje dosyasından bir bağımlılığı kaldırmak, `<PackageReference>` proje dosyasından kaldırmayı içerir.
