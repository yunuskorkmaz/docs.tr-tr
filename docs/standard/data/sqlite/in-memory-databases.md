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

SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlarıdır. Bellek tesisi `:memory:` oluşturmak için özel veri kaynağı dosya adını kullanın. Bağlantı kapatıldığında, veritabanı silinir. Kullanırken, `:memory:`her bağlantı kendi veritabanını oluşturur.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Paylaşılabilir bellek içi veritabanları

Bellek içi veritabanları kullanılarak `Mode=Memory` ve `Cache=Shared` bağlantı dizesinde birden çok bağlantı arasında paylaşılabilir. Anahtar `Data Source` kelime, bellek veritabanına bir ad vermek için kullanılır. Aynı adı kullanan bağlantı dizeleri aynı bellek veritabanına erişecektir. Veritabanı, en az bir bağlantı açık kaldığı sürece devam eder. Bunu gösteren bir [örnek](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) GitHub'da kullanılabilir.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
