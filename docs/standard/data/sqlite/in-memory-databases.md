---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 8bc96811753e49f740a33a2e78f955483efcf04b
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190352"
---
# <a name="in-memory-databases"></a>Bellek içi veritabanları

SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır. Bellek içi veritabanı oluşturmak için özel veri kaynağı dosya adını kullanın `:memory:` . Bağlantı kapatıldığında veritabanı silinir. Kullanırken `:memory:` , her bağlantı kendi veritabanını oluşturur.

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Paylaşılabilir bellek içi veritabanları

Bellek içi veritabanları `Mode=Memory` , bağlantı dizesinde ve kullanılarak birden çok bağlantı arasında paylaşılabilir `Cache=Shared` . `Data Source`Anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır. Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir. En az bir bağlantı açık kaldığı sürece veritabanı devam eder. GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) .

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
