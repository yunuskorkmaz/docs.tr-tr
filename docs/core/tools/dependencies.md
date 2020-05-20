---
title: ''
description: ''
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: ''
ms.openlocfilehash: 667b2d4d68edd82a4d18c370e45ea18f4d4b379a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702846"
---
# <a name="manage-dependencies-in-net-core-applications"></a>.NET Core uygulamalarında bağımlılıkları yönetme

Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.

## <a name="the-packagereference-element"></a>\<Packagereference> öğesi

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

Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır. `$(TargetFramework)`Koşulunda, projede ayarlanmış bir MSBuild özelliği bulunur. En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.

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

* [Proje dosyalarında paket başvuruları](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [dotnet list packagekomutundaki](dotnet-list-package.md)
