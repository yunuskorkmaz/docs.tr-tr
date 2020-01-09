---
title: Veri türleri
ms.date: 12/13/2019
description: Desteklenen veri türlerini ve bunların çevresindeki bazı sınırlamaları açıklar.
ms.openlocfilehash: ae70cb91a5a6d9cfed45a5a47dda25a70362871e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447183"
---
# <a name="data-types"></a>Veri türleri

SQLite yalnızca dört temel veri türüne sahiptir: tamsayı, gerçek, metın ve BLOB. Veritabanı değerlerini `object` olarak döndüren API 'Ler, yalnızca bu dört türden birini döndürür. Ek .NET türleri Microsoft. Data. SQLite tarafından desteklenir, ancak değerler bu türler ve dört temel türden biri arasında sonuç olarak zorlanır.

| .NET           | SQLite  | Açıklamalar                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boole değeri        | INTEGER | `0` veya `1`                                                    |
| Bayt           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | yyyy-AA-GG SS: DD: ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | yyyy-AA-GG SS: DD: ss. FFFFFFFzzz                                |
| Ondalık        | TEXT    | `0.0###########################` biçimi. GERÇEK, kayıplı olur. |
| Çift         | REAL    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Tek         | REAL    |                                                               |
| Dize         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh: mm: ss. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt64         | INTEGER | Büyük değer taşması                                         |

## <a name="alternative-types"></a>Alternatif türler

Bazı .NET türleri alternatif SQLite türlerinden okunabilir. Parametreler, bu alternatif türleri kullanacak şekilde de yapılandırılabilir. Daha fazla bilgi için bkz. [Parametreler](parameters.md#alternative-types).

| .NET           | SQLite  | Açıklamalar          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | REAL    | Jülyen gün değeri |
| DateTimeOffset | REAL    | Jülyen gün değeri |
| Guid           | BLOB    |                  |
| TimeSpan       | REAL    | Gün cinsinden          |

Örneğin, aşağıdaki sorgu, sonuç kümesindeki gerçek bir sütundan bir TimeSpan değeri okur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Sütun türleri

SQLite, bir değer türünün depolandığı sütun değil, değerin kendisi ile ilişkilendirildiği dinamik bir tür sistemi kullanır. Dilediğiniz sütun türü adını kullanabilirsiniz. Microsoft. Data. SQLite, bu adlara ek semantik hiçbiri uygulamaz.

Sütun türü adının [tür benzeşimi](https://www.sqlite.org/datatype3.html#type_affinity)üzerinde bir etkisi vardır. Tek bir yaygın Gotcha, bir DIZE türü kullanmanın değerleri ıNTEGER veya REAL değerine dönüştürmeye çalışır, bu da beklenmedik sonuçlara yol açabilir. Yalnızca dört temel SQLite tür adı kullanmanızı öneririz: tamsayı, gerçek, metın ve BLOB.

SQLite, uzunluk, duyarlık ve ölçek gibi tür modellerini belirtmenize izin verir, ancak bunlar veritabanı altyapısı tarafından zorlanmaz. Uygulamanızı zormaktan sorumludur.

## <a name="see-also"></a>Ayrıca bkz.

- [SQLite Içindeki veri türleri](https://www.sqlite.org/datatype3.html)
