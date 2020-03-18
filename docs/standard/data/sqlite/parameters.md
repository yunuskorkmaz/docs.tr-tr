---
title: Parametreler
ms.date: 12/13/2019
description: SQL parametrelerinin nasıl kullanılacağını öğrenin.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400458"
---
# <a name="parameters"></a>Parametreler

Parametreler SQL enjeksiyon saldırılarına karşı korumak için kullanılır. Kullanıcı girdisini SQL deyimleriyle darletmek yerine, girişin yalnızca gerçek bir değer olarak ele alınmasını ve hiçbir zaman gerçekleştirilmemesini sağlamak için parametreleri kullanın. SQLite'de parametrelergenellikle SQL deyimlerinde gerçek bir ifadeye izin verilen her yerde izin verilir.

Parametreler `:`, `@`veya `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

.NET değerlerinin SQLite değerlerine nasıl eşlendirildiklerine ilişkin ayrıntılar için [veri türlerine](types.md) bakın.

## <a name="truncation"></a>Kesilme

TEXT <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> ve BLOB değerlerini doyurmak için özelliği kullanın.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Alternatif türler

Bazen, alternatif bir SQLite türü kullanmak isteyebilirsiniz. <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> Özelliği ayarlayarak bunu yapın.

Aşağıdaki alternatif tür eşlemeleri kullanılabilir. Varsayılan eşlemeler için [Bkz. Veri türleri.](types.md)

| Değer          | SqliteType | Açıklamalar          |
| -------------- | ---------- | ---------------- |
| Char           | Tamsayı    | UTF-16           |
| DateTime       | Gerçek       | Jülyen gün değeri |
| DateTimeOffset | Gerçek       | Jülyen gün değeri |
| Guid           | Blob       |                  |
| TimeSpan       | Gerçek       | Gün içinde          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Çıktı parametreleri

SQLite çıkış parametrelerini desteklemez. Bunun yerine sorgu sonuçlarında değerleri döndürün.

## <a name="see-also"></a>Ayrıca bkz.

* [Veri türleri](types.md)
