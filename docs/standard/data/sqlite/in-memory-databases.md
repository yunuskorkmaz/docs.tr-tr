---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391214"
---
# <a name="in-memory-databases"></a>Bellek içi veritabanları

SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır. Bellek içi veritabanı oluşturmak için özel `:memory:` veri kaynağı dosya adını kullanın. Bağlantı kapatıldığında veritabanı silinir. Kullanırken `:memory:`, her bağlantı kendi veritabanını oluşturur.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Paylaşılabilir bellek içi veritabanları

Bellek içi veritabanları, bağlantı dizesinde ve `Mode=Memory` `Cache=Shared` kullanılarak birden çok bağlantı arasında paylaşılabilir. `Data Source` Anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır. Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir. En az bir bağlantı açık kaldığı sürece veritabanı devam eder. GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) .

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
