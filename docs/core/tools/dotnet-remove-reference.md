---
title: dotnet kaldırma başvuru komutu
description: Dotnet kaldırma başvuru komutu proje başvurularını kaldırmak için uygun bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503623"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet remove reference`- Projeden projeye başvuruları kaldırır.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet remove reference` proje başvurularını projeden kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT`

Hedef proje dosyası. Belirtilmemişse, komut geçerli dizini arar.

`PROJECT_REFERENCES`

Kaldırılacak proje-proje (P2P) başvuruları. Bir veya birden çok proje belirtebilirsiniz. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) Unix/Linux tabanlı terminallerde desteklenir.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-f|--framework <FRAMEWORK>`**

  Başvuruyu yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken kaldırır.

## <a name="examples"></a>Örnekler

- Proje başvurularını belirtilen projeden kaldırma:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Geçerli dizinde projeden birden çok proje öncesini kaldırın:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Unix/Linux'ta glob deseni kullanarak birden çok proje referansı kaldırın:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
