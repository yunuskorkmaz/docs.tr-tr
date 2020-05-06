---
title: .NET Core 'da bağımlılıkları yönetme
description: Bir .NET Core uygulaması için proje bağımlılıklarının nasıl yönetileceğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 3e1d807ea69e66e31b277a92cd6a1dc0e76531b5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795553"
---
# <a name="manage-dependencies-in-net-core-applications"></a>.NET Core uygulamalarında bağımlılıkları yönetme

Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.

## <a name="the-packagereference-element"></a>\<Packagereference> öğesi

`<PackageReference>` Proje dosyası öğesi aşağıdaki yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

`Include` Öznitelik, projeye eklenecek paketin kimliğini belirtir. `Version` Öznitelik alınacak sürümü belirtir. Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.

> [!NOTE]
> Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.

Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır. Koşulunda `$(TargetFramework)` , projede ayarlanmış bir MSBuild özelliği bulunur. En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bir bağımlılık ekleyin

Bir bağımlılık eklemek için bir `<PackageReference>` `<ItemGroup>` öğe içine bir öğe ekleyin. Var olan `<ItemGroup>` bir veya yeni bir tane oluşturabilirsiniz. Aşağıdaki örnek, tarafından `dotnet new console`oluşturulan varsayılan konsol uygulaması projesini kullanır:

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

Bir bağımlılık eklemek için aşağıdaki örnekte gösterildiği [dotnet add package](dotnet-add-package.md) gibi komutunu çalıştırın:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.

## <a name="remove-a-dependency-by-using-the-cli"></a>CLı kullanarak bir bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için, aşağıdaki örnekte [dotnet remove package](dotnet-remove-package.md) gösterildiği gibi komutunu çalıştırın:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Ayrıca bkz.

* [Proje dosyalarında paket başvuruları](../project-sdk/msbuild-props.md#reference-properties)
* [dotnet list packagekomutundaki](dotnet-remove-package.md)
