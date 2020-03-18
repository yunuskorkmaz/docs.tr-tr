---
title: dotnet listesi referans komutu
description: Dotnet listesi başvuru komutu, proje başvurularını projeye listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503710"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet list reference`- Projeden projeye referansları listeler.

## <a name="synopsis"></a>Özet

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

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
