---
title: .NET 'teki bağımlılıkları yönetme
description: Bir .NET uygulaması için proje bağımlılıklarının nasıl yönetileceğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 01/28/2021
ms.openlocfilehash: 03311902e99962553b5b740a285021f27d94bfbc
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759709"
---
# <a name="manage-dependencies-in-net-applications"></a>.NET uygulamalarında bağımlılıkları yönetme

Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.

## <a name="the-packagereference-element"></a>\<PackageReference>Öğe

`<PackageReference>`Proje dosyası öğesi aşağıdaki yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

`Include`Öznitelik, projeye eklenecek PAKETIN kimliğini belirtir. `Version`Öznitelik alınacak sürümü belirtir. Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.

> [!NOTE]
> Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.

Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır. `$(TargetFramework)`Koşulunda, projede ayarlanmış bir MSBuild özelliği bulunur. En yaygın .NET uygulamaları için bunu yapmanız gerekmez.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bir bağımlılık ekleyin

Bir bağımlılık eklemek için bir `<PackageReference>` öğe içine bir öğe ekleyin `<ItemGroup>` . Var olan bir `<ItemGroup>` veya yeni bir tane oluşturabilirsiniz. Aşağıdaki örnek, tarafından oluşturulan varsayılan konsol uygulaması projesini kullanır `dotnet new console` :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a>CLı kullanarak bağımlılık ekleme

Bir bağımlılık eklemek için [dotnet add package](dotnet-add-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.

## <a name="remove-a-dependency-by-using-the-cli"></a>CLı kullanarak bir bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için, [dotnet remove package](dotnet-remove-package.md) Aşağıdaki örnekte gösterildiği gibi komutunu çalıştırın:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Ayrıca bkz.

* [Proje dosyalarında paket başvuruları](../project-sdk/msbuild-props.md#reference-properties)
* [dotnet list package komutundaki](dotnet-list-package.md)
