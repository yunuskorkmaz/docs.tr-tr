---
title: dotnet listesi referans komutu
description: Dotnet listesi başvuru komutu, proje başvurularını projeye listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463653"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet list reference`- Projeden projeye referansları listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet list reference` belirli bir proje veya çözüm için proje başvurularını listelemek için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

* **`PROJECT | SOLUTION`**

  Başvuruları listeleme için kullanılacak proje veya çözüm dosyasını belirtir. Belirtilmemişse, komut bir proje dosyası için geçerli dizini arar.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

* Belirtilen proje için proje başvurularını listele:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Proje başvurularını geçerli dizindeki listele:

  ```dotnetcli
  dotnet list reference
  ```
