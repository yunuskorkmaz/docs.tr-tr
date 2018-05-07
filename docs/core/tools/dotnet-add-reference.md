---
title: DotNet-başvuru komut - .NET Core CLI ekleme
description: Dotnet ekleyin başvuru komutu proje için proje başvuruları eklemek için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.openlocfilehash: ee9c058b83238655bd90a4bf5c809a9d0e4c13d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-add-reference"></a>DotNet-Başvuru Ekle

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet add reference` -Proje Proje (P2P) başvuruları ekler.

## <a name="synopsis"></a>Özet

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet add reference` Komutu proje başvuruları bir proje eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) öğeleri proje dosyasına eklenir.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`PROJECT`

Proje dosyası belirtir. Belirtilmezse, komut için geçerli dizin arar.

`PROJECT_REFERENCES`

Eklemek için proje proje (P2P) başvuruyor. Bir veya daha fazla projeleri belirtin. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-f|--framework <FRAMEWORK>`

Proje başvuruları yalnızca belirli bir hedeflerken ekler [framework](../../standard/frameworks.md).

## <a name="examples"></a>Örnekler

Proje başvurusu ekleyin:

`dotnet add app/app.csproj reference lib/lib.csproj`

Birden çok proje başvuruları projeye geçerli dizinde ekleyin:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Linux/Unix üzerinde genelleme desenini kullanarak birden çok proje başvurularını ekleyin:

`dotnet add app/app.csproj reference **/*.csproj`
