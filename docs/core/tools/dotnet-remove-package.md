---
title: DotNet paket Kaldır komutu
description: DotNet Remove Package komutu, bir projeye NuGet paket başvurusunu kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503638"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet remove package`-paket başvurusunu bir proje dosyasından kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet remove package` komutu bir projeden NuGet paket başvurusunu kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT`

Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

`PACKAGE_NAME`

Kaldırılacak paket başvurusu.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- `Newtonsoft.Json` NuGet paketini geçerli dizindeki bir projeden kaldır:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
