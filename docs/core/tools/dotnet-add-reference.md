---
title: DotNet-başvuru komutu Ekle
description: DotNet başvuru komutu, proje başvurularına proje eklemek için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 867596058aad8f9c38918e6d6657709d0d0699b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784053"
---
# <a name="dotnet-add-reference"></a>DotNet-başvuru Ekle

**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet add reference`-Projeden projeye (P2P) başvuruları ekler.

## <a name="synopsis"></a>Özeti

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Açıklama

Komut `dotnet add reference` , projeye proje başvuruları eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra `<ProjectReference>` öğeler proje dosyasına eklenir.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

* **`PROJECT_REFERENCES`**

  Eklenecek projeden projeye (P2P) başvuruları. Bir veya daha fazla proje belirtin. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken proje başvuruları ekler.

* **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 3,0 SDK 'dan beri kullanılabilir.

## <a name="examples"></a>Örnekler

* Proje başvurusu Ekle:

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Geçerli dizindeki projeye birden çok proje başvurusu ekleyin:

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Linux/Unix üzerinde glob bir model kullanarak birden çok proje başvurusu ekleme:

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
