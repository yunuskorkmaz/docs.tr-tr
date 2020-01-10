---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 16a9b6536fbfede203c24b757e96e28e7c49dc05
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777411"
---
# <a name="in-memory-databases"></a>Bellek içi veritabanları

SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır. Bellek içi veritabanı oluşturmak için `:memory:` özel veri kaynağı dosya adı kullanın. Bağlantı kapatıldığında veritabanı silinir. `:memory:`kullanırken, her bağlantı kendi veritabanını oluşturur.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Paylaşılabilir bellek içi veritabanları

Bellek içi veritabanları, bağlantı dizesinde `Mode=Memory` ve `Cache=Shared` kullanılarak birden çok bağlantı arasında paylaşılabilir. `Data Source` anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır. Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir. En az bir bağlantı açık kaldığı sürece veritabanı devam eder. GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) .

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
