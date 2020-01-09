---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447246"
---
# <a name="in-memory-databases"></a>Bellek içi veritabanları

SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır. Bellek içi veritabanı oluşturmak için `:memory:` özel veri kaynağı dosya adı kullanın. Bağlantı kapatıldığında veritabanı silinir. `:memory:`kullanırken, her bağlantı kendi veritabanını oluşturur.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Paylaşılabilir bellek içi veritabanları

Bellek içi veritabanları, bağlantı dizesinde `Mode=Memory` ve `Cache=Shared` kullanılarak birden çok bağlantı arasında paylaşılabilir. `Data Source` anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır. Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir. En az bir bağlantı açık kaldığı sürece veritabanı devam eder. GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) .

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
