---
title: .NET Core 'da bağımlılıkları yönetme
description: Bir .NET Core uygulaması için proje bağımlılıklarının nasıl yönetileceğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157251"
---
# <a name="manage-dependencies-in-net-core-applications"></a>.NET Core uygulamalarında bağımlılıkları yönetme

Bu makalede, proje dosyasını düzenleyerek veya CLı kullanarak bağımlılık ekleme ve kaldırma işlemleri açıklanmaktadır.

## <a name="the-packagereference-element"></a>\<PackageReference > öğesi

`<PackageReference>` proje dosyası öğesi aşağıdaki yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

`Include` özniteliği, projeye eklenecek paketin KIMLIĞINI belirtir. `Version` özniteliği alınacak sürümü belirtir. Sürümler, [NuGet sürüm kuralları](/nuget/create-packages/dependency-versions#version-ranges)başına belirtilmiştir.

> [!NOTE]
> Proje dosyası söz dizimine alışkın değilseniz, daha fazla bilgi için [MSBuild proje başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.

Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Önceki örnekteki bağımlılık yalnızca derleme söz konusu hedef için varsa geçerli olacaktır. Koşuldaki `$(TargetFramework)`, projede ayarlanmış bir MSBuild özelliğidir. En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bir bağımlılık ekleyin

Bir bağımlılık eklemek için, bir `<ItemGroup>` öğesinin içine bir `<PackageReference>` öğesi ekleyin. Var olan bir `<ItemGroup>` ekleyebilir veya yeni bir tane oluşturabilirsiniz. Aşağıdaki örnek, `dotnet new console`tarafından oluşturulan varsayılan konsol uygulaması projesini kullanır:

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

Bir bağımlılık eklemek için, aşağıdaki örnekte gösterildiği gibi [dotnet add package](dotnet-add-package.md) komutunu çalıştırın:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.

## <a name="remove-a-dependency-by-using-the-cli"></a>CLı kullanarak bir bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için, aşağıdaki örnekte gösterildiği gibi [dotnet remove package](dotnet-remove-package.md) komutunu çalıştırın:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Ayrıca bkz.

* [Proje dosyalarındaki NuGet paketleri](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list package komutu](dotnet-remove-package.md)
