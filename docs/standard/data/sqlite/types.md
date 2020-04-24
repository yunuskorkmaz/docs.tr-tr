---
title: Veri türleri
ms.date: 12/13/2019
description: Desteklenen veri türlerini ve bunların çevresindeki bazı sınırlamaları açıklar.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389036"
---
# <a name="data-types"></a>Veri türleri

SQLite yalnızca dört temel veri türüne sahiptir: tamsayı, gerçek, metın ve BLOB. Veritabanı değerlerini olarak döndüren API 'Ler `object` , yalnızca bu dört türden birini döndürür. Ek .NET türleri Microsoft. Data. SQLite tarafından desteklenir, ancak değerler bu türler ve dört temel türden biri arasında sonuç olarak zorlanır.

| .NET           | SQLite  | Açıklamalar                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boole        | TAMSAYI | `0` veya `1`                                                    |
| Bayt           | TAMSAYI |                                                               |
| Byte []         | Bun    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | yyyy-AA-GG SS: DD: ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | yyyy-AA-GG SS: DD: ss. FFFFFFFzzz                                |
| Ondalık        | TEXT    | `0.0###########################`formatını. GERÇEK, kayıplı olur. |
| Çift         | GERÇEK SAYI    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | TAMSAYI |                                                               |
| Int32          | TAMSAYI |                                                               |
| Int64          | TAMSAYI |                                                               |
| SByte          | TAMSAYI |                                                               |
| Tek         | GERÇEK SAYI    |                                                               |
| Dize         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh: mm: ss. fffffff                                            |
| UInt16         | TAMSAYI |                                                               |
| UInt32         | TAMSAYI |                                                               |
| UInt64         | TAMSAYI | Büyük değer taşması                                         |

## <a name="alternative-types"></a>Alternatif türler

Bazı .NET türleri alternatif SQLite türlerinden okunabilir. Parametreler, bu alternatif türleri kullanacak şekilde de yapılandırılabilir. Daha fazla bilgi için bkz. [Parametreler](parameters.md#alternative-types).

| .NET           | SQLite  | Açıklamalar          |
| -------------- | ------- | ---------------- |
| Char           | TAMSAYI | UTF-16           |
| DateTime       | GERÇEK SAYI    | Jülyen gün değeri |
| DateTimeOffset | GERÇEK SAYI    | Jülyen gün değeri |
| Guid           | Bun    |                  |
| TimeSpan       | GERÇEK SAYI    | Gün cinsinden          |

Örneğin, aşağıdaki sorgu, sonuç kümesindeki gerçek bir sütundan bir TimeSpan değeri okur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Sütun türleri

SQLite, bir değer türünün depolandığı sütun değil, değerin kendisi ile ilişkilendirildiği dinamik bir tür sistemi kullanır. Dilediğiniz sütun türü adını kullanabilirsiniz. Microsoft. Data. SQLite, bu adlara ek semantik hiçbiri uygulamaz.

Sütun türü adının [tür benzeşimi](https://www.sqlite.org/datatype3.html#type_affinity)üzerinde bir etkisi vardır. Tek bir yaygın Gotcha, bir DIZE türü kullanmanın değerleri ıNTEGER veya REAL değerine dönüştürmeye çalışır, bu da beklenmedik sonuçlara yol açabilir. Yalnızca dört temel SQLite tür adı kullanmanızı öneririz: tamsayı, gerçek, metın ve BLOB.

SQLite, uzunluk, duyarlık ve ölçek gibi tür modellerini belirtmenize izin verir, ancak bunlar veritabanı altyapısı tarafından zorlanmaz. Uygulamanızı zormaktan sorumludur.

## <a name="see-also"></a>Ayrıca bkz.

- [SQLite Içindeki veri türleri](https://www.sqlite.org/datatype3.html)
