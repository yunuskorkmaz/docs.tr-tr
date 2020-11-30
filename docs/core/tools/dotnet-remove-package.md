---
title: DotNet paket Kaldır komutu
description: DotNet Remove Package komutu, bir projeye NuGet paket başvurusunu kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2020
ms.locfileid: "81463452"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet remove package` -Bir proje dosyasından paket başvurusunu kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a>Description

`dotnet remove package`Komut, bir projeden NuGet paket başvurusunu kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

`PACKAGE_NAME`

Kaldırılacak paket başvurusu.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- `Newtonsoft.Json`NuGet paketini geçerli dizindeki bir projeden kaldır:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
