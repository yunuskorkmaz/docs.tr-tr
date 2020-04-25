---
title: DotNet Remove başvuru komutu
description: DotNet Remove Reference komutu, projeyi Proje başvurularına kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158339"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet remove reference`-Projeden projeye (P2P) başvurularını kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a>Açıklama

Komut `dotnet remove reference` , bir projeden proje başvurularını kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT`

Hedef proje dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

`PROJECT_REFERENCES`

Kaldırılacak projeden projeye (P2P) başvuruları. Bir veya daha fazla proje belirtebilirsiniz. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-f|--framework <FRAMEWORK>`**

  Başvuruyu yalnızca, tfd biçimini kullanarak belirli bir [çerçeveyi](../../standard/frameworks.md) hedeflerken kaldırır.

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
