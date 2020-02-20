---
title: DotNet Remove başvuru komutu
description: DotNet Remove Reference komutu, projeyi Proje başvurularına kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503623"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet remove reference`-projeden projeye başvuruları kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet remove reference` komutu bir projeden proje başvurularını kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT`

Hedef proje dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

`PROJECT_REFERENCES`

Kaldırılacak projeden projeye (P2P) başvuruları. Bir veya daha fazla proje belirtebilirsiniz. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken başvuruyu kaldırır.

## <a name="examples"></a>Örnekler

- Belirtilen projeden bir proje başvurusunu kaldır:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Geçerli dizindeki projeden birden çok proje başvurusu kaldır:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- UNIX/Linux 'ta glob modelini kullanarak birden çok proje başvurusu kaldırma:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
