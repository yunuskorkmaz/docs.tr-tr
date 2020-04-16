---
title: dotnet kaldırma paket komutu
description: Dotnet kaldırma paketi komutu, NuGet paket başvurularını bir projeye kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463452"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet remove package`- Paket başvurularını proje dosyasından kaldırır.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet remove package` bir Projeden NuGet paket başvurularını kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT`

Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizini arar.

`PACKAGE_NAME`

Kaldırılacak paket başvurusu.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- Geçerli `Newtonsoft.Json` dizindeki projeden NuGet paketini kaldırın:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
