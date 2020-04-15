---
title: Veri türleri
ms.date: 12/13/2019
description: Desteklenen veri türlerini ve bunların etrafındaki bazı sınırlamaları açıklar.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389036"
---
# <a name="data-types"></a>Veri türleri

SQLite yalnızca dört ilkel veri türüne sahiptir: INTEGER, REAL, TEXT ve BLOB. Veritabanı değerlerini bu `object` dört türden yalnızca biri döndürülen API'ler. Ek .NET türleri Microsoft.Data.Sqlite tarafından desteklenir, ancak değerler sonuçta bu türler ile dört ilkel tür arasında zorlanır.

| .NET           | SQLite  | Açıklamalar                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boole        | TAMSAYI | `0` veya `1`                                                    |
| Bayt           | TAMSAYI |                                                               |
| Bayt[]         | Blob    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFFzzz                                |
| Ondalık        | TEXT    | `0.0###########################`Biçim. REAL kayıp olur. |
| Çift         | GERÇEK SAYI    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | TAMSAYI |                                                               |
| Int32          | TAMSAYI |                                                               |
| Int64          | TAMSAYI |                                                               |
| SByte          | TAMSAYI |                                                               |
| Tek         | GERÇEK SAYI    |                                                               |
| Dize         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d.hh:mm:ss.fffffff                                            |
| UInt16         | TAMSAYI |                                                               |
| UInt32         | TAMSAYI |                                                               |
| UInt64         | TAMSAYI | Büyük değerler taşması                                         |

## <a name="alternative-types"></a>Alternatif türler

Bazı .NET türleri alternatif SQLite türlerinden okunabilir. Parametreler bu alternatif türleri kullanacak şekilde de yapılandırılabilir. Daha fazla bilgi için [Parametreler'e](parameters.md#alternative-types)bakın.

| .NET           | SQLite  | Açıklamalar          |
| -------------- | ------- | ---------------- |
| Char           | TAMSAYI | UTF-16           |
| DateTime       | GERÇEK SAYI    | Jülyen gün değeri |
| DateTimeOffset | GERÇEK SAYI    | Jülyen gün değeri |
| Guid           | Blob    |                  |
| TimeSpan       | GERÇEK SAYI    | Gün içinde          |

Örneğin, aşağıdaki sorgu, sonuç kümesindeki GERÇEK sütundaki TimeSpan değerini okur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Sütun türleri

SQLite, değer türünün depolandığı sütunla değil, değerin kendisiyle ilişkili olduğu dinamik bir tür sistemi kullanır. İstediğiniz sütun türü adını kullanmakta özgürsunuz. Microsoft.Data.Sqlite bu adlara ek semantik uygulamaz.

Sütun türü adı [türü afinite](https://www.sqlite.org/datatype3.html#type_affinity)üzerinde bir etkisi var. Yaygın bir gotcha STRING bir sütun türünü kullanarak beklenmeyen sonuçlara yol açabilir INTEGER veya REAL, değerleri dönüştürmek için çalışacağız olmasıdır. Yalnızca dört ilkel SQLite türü adlarını kullanmanızı öneririz: INTEGER, REAL, TEXT ve BLOB.

SQLite, uzunluk, kesinlik ve ölçek gibi tür yönlerini belirtmenize olanak tanır, ancak bunlar veritabanı altyapısı tarafından zorlanmaz. Uygulamanız bunları uygulamadan sorumludur.

## <a name="see-also"></a>Ayrıca bkz.

- [SQLite'de Veri Tipleri](https://www.sqlite.org/datatype3.html)
