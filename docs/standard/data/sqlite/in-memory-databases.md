---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: fbda5787d95a9ce462752b985f847af0b0551fa6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555373"
---
# <a name="in-memory-databases"></a>Bellek içi veritabanları

SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır. Bellek içi veritabanı oluşturmak için özel veri kaynağı dosya adını kullanın `:memory:` . Bağlantı kapatıldığında veritabanı silinir. Kullanırken `:memory:` , her bağlantı kendi veritabanını oluşturur.

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Paylaşılabilir bellek içi veritabanları

Bellek içi veritabanları `Mode=Memory` , bağlantı dizesinde ve kullanılarak birden çok bağlantı arasında paylaşılabilir `Cache=Shared` . `Data Source`Anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır. Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir. En az bir bağlantı açık kaldığı sürece veritabanı devam eder. GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) .

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
