---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802758"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet list reference`-Projeden projeye başvuruları listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a>Açıklama

`dotnet list reference`Komut, belirli bir proje için proje başvurularını listelemek üzere uygun bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız değişkenler

* **`PROJECT`**

  Üzerinde çalışılacak proje dosyası. Bir dosya belirtilmemişse, komut geçerli dizinde bir arama yapılır.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

* Belirtilen proje için proje başvurularını listeleyin:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Geçerli dizindeki projenin proje başvurularını listeleyin:

  ```dotnetcli
  dotnet list reference
  ```
