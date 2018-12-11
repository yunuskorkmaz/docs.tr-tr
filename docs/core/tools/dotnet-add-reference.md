---
title: DotNet-başvuru komut ekleme
description: Dotnet ekleyin başvuru komut projeden projeye başvurular eklemek için uygun bir seçenek sağlar.
ms.date: 12/04/2018
ms.openlocfilehash: 8df9fa3c9469f74b27a9cb8120936f03532b016c
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169777"
---
# <a name="dotnet-add-reference"></a>DotNet-Başvuru Ekle

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet add reference` -Projeler (P2P) başvuruları ekler.

## <a name="synopsis"></a>Özeti

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet add reference` Komutu, bir proje proje başvurular eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) öğeleri, proje dosyasına eklenir.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmezse, komut için geçerli dizinde arar.

* **`PROJECT_REFERENCES`**

  Eklenecek proje proje (P2P) başvuruyor. Bir veya daha fazla proje belirtin. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir hedeflenirken proje başvuruları ekler [framework](../../standard/frameworks.md).

## <a name="examples"></a>Örnekler

* Bir proje başvurusu Ekle:

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Geçerli dizinde birden çok proje başvuruları projeye ekleyin:

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Linux/UNIX Glob deseni kullanılarak birden çok proje başvurularını ekleyin:

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```