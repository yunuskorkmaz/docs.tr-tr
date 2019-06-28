---
title: DotNet-başvuru komut ekleme
description: Dotnet ekleyin başvuru komut projeden projeye başvurular eklemek için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 6e0ca40e701b62dcc18147f9de83cafa6aa2f50f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421999"
---
# <a name="dotnet-add-reference"></a>DotNet-Başvuru Ekle

**Bu makale için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet add reference` -Projeler (P2P) başvuruları ekler.

## <a name="synopsis"></a>Synopsis

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

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

* **`--interactive`**

  Durdurmak ve kullanıcı girişi veya eylem (örneğin, kimlik doğrulamasını tamamlamak için) için beklemek için komutu sağlar. .NET Core SDK 3.0 bu yana kullanılabilir.

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
