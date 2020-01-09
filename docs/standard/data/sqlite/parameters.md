---
title: Parametreler
ms.date: 12/13/2019
description: SQL parametrelerini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447190"
---
# <a name="parameters"></a>Parametreler

Parametreleri SQL ekleme saldırılarına karşı korumak için kullanılır. Kullanıcı girişini SQL deyimleriyle birleştirerek, girişin yalnızca bir sabit değer olarak değerlendirildiğinden ve hiçbir zaman yürütüldüğünden emin olmak için parametreleri kullanın. SQLite 'ta, parametrelere genellikle SQL deyimlerde bir sabit değere izin verilen her yerde izin verilir.

Parametrelere `:`, `@`veya `$`ön eki uygulanabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

.NET değerlerinin SQLite değerlerine nasıl eşlendiğine ilişkin ayrıntılar için bkz. [veri türleri](types.md) .

## <a name="truncation"></a>Kesildi

METIN ve BLOB değerlerini kesmek için <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> özelliğini kullanın.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Alternatif türler

Bazen alternatif bir SQLite türü kullanmak isteyebilirsiniz. <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> özelliğini ayarlayarak bunu yapın.

Aşağıdaki alternatif tür eşlemeleri kullanılabilir. Varsayılan eşlemeler için bkz. [veri türleri](types.md).

| Değer          | SqliteType | Açıklamalar          |
| -------------- | ---------- | ---------------- |
| Char           | Tamsayı    | UTF-16           |
| DateTime       | Gerçek       | Jülyen gün değeri |
| DateTimeOffset | Gerçek       | Jülyen gün değeri |
| Guid           | Blob       |                  |
| TimeSpan       | Gerçek       | Gün cinsinden          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Çıktı parametreleri

SQLite çıkış parametrelerini desteklemiyor. Bunun yerine sorgu sonuçlarındaki değerleri döndürün.

## <a name="see-also"></a>Ayrıca bkz.

* [Veri türleri](types.md)
