---
title: Parametreler
ms.date: 12/13/2019
description: SQL parametrelerini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: b24610a5cb65e2b24171452acef9bf55b4995431
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768956"
---
# <a name="parameters"></a>Parametreler

Parametreleri SQL ekleme saldırılarına karşı korumak için kullanılır. Kullanıcı girişini SQL deyimleriyle birleştirerek, girişin yalnızca bir sabit değer olarak değerlendirildiğinden ve hiçbir zaman yürütüldüğünden emin olmak için parametreleri kullanın. SQLite 'ta, parametrelere genellikle SQL deyimlerde bir sabit değere izin verilen her yerde izin verilir.

Parametrelere, ya da ön eki `:` uygulanabilir `@` `$` .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

.NET değerlerinin SQLite değerlerine nasıl eşlendiğine ilişkin ayrıntılar için bkz. [veri türleri](types.md) .

## <a name="truncation"></a>Kesildi

<xref:Microsoft.Data.Sqlite.SqliteParameter.Size>Metin ve BLOB değerlerini kesmek için özelliğini kullanın.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Size = 30;
```

## <a name="alternative-types"></a>Alternatif türler

Bazen alternatif bir SQLite türü kullanmak isteyebilirsiniz. Özelliği ayarlayarak bunu yapın <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> .

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
