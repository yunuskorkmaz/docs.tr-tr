---
title: .NET Core'daki bağımlılıkları yönetme
description: .NET Core uygulaması için proje bağımlılıklarının nasıl yönetilmeye başlanması gerektiğini açıklar.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399149"
---
# <a name="manage-dependencies-in-net-core-applications"></a>.NET Core uygulamalarındaki bağımlılıkları yönetme

Bu makalede, proje dosyasını düzenleyerek veya CLI'yi kullanarak bağımlılıkların nasıl ekleyeceğinive kaldırılacakları açıklanmaktadır.

## <a name="the-packagereference-element"></a>\<PackageReference> öğesi

`<PackageReference>` Proje dosyası öğesi aşağıdaki yapıya sahiptir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Öznitelik, `Include` projeye eklenecek paketin kimliğini belirtir. Öznitelik, `Version` elde etmek için sürümü belirtir. Sürümler [NuGet sürüm kurallarına](/nuget/create-packages/dependency-versions#version-ranges)göre belirtilir.

> [!NOTE]
> Proje dosyası sözdizimini bilmiyorsanız, daha fazla bilgi için [MSBuild proje başvuru](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgelerine bakın.

Aşağıdaki örnekte gösterildiği gibi, yalnızca belirli bir hedefte kullanılabilen bir bağımlılık eklemek için koşulları kullanın:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Önceki örnekteki bağımlılık, yalnızca bu hedef için yapı gerçekleşiyorsa geçerli olacaktır. Durumda `$(TargetFramework)` projede ayarlanan bir MSBuild özelliğidir. En yaygın .NET Core uygulamaları için bunu yapmanız gerekmez.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bağımlılık ekleme

Bağımlılık eklemek için, bir `<PackageReference>` `<ItemGroup>` öğenin içine bir öğe ekleyin. Varolan `<ItemGroup>` bir taneye ekleyebilir veya yeni bir tane oluşturabilirsiniz. Aşağıdaki örnekte, aşağıdakiler tarafından `dotnet new console`oluşturulan varsayılan konsol uygulama projesi kullanır:

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

## <a name="add-a-dependency-by-using-the-cli"></a>CLI'yi kullanarak bağımlılık ekleme

Bağımlılık eklemek için aşağıdaki [dotnet add package](dotnet-add-package.md) örnekte gösterildiği gibi komutu çalıştırın:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Proje dosyasını düzenleyerek bir bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için `<PackageReference>` öğesini proje dosyasından kaldırın.

## <a name="remove-a-dependency-by-using-the-cli"></a>CLI'yi kullanarak bir bağımlılığı kaldırma

Bir bağımlılığı kaldırmak için [dotnet remove package](dotnet-remove-package.md) aşağıdaki örnekte gösterildiği gibi komutu çalıştırın:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Ayrıca bkz.

* [Proje dosyalarındaki Paketleri NuGet](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list packageKomut](dotnet-remove-package.md)
