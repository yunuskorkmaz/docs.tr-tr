---
title: Harmanlama
ms.date: 12/13/2019
description: Özel bir harmanlama sırası oluşturmayı öğrenin.
ms.openlocfilehash: 9cc574a75c8f5347dd9bb44e36af72e50afa57b4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777383"
---
# <a name="collation"></a>Harmanlama

Harmanlama dizileri, sıralama ve eşitlik belirlenmesi için metın değerleri karşılaştırılırken SQLite tarafından kullanılır. SQL sorgularında sütun veya işlem başına oluşturma sırasında hangi harmanlamayı kullanacağınızı belirtebilirsiniz. SQLite varsayılan olarak üç harmanlama dizisi içerir.

| Harmanlama | Açıklama                               |
| --------- | ----------------------------------------- |
| RTRIM     | Sondaki boşluğu yoksayar               |
| NOCASE    | ASCII karakterleri A-Z için büyük/küçük harfe duyarsız |
| BINARY    | Büyük/küçük harfe duyarlı. Baytları doğrudan karşılaştırır   |

## <a name="custom-collation"></a>Özel harmanlama

Ayrıca, kendi harmanlama dizlerinizi tanımlayabilir veya <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>kullanarak yerleşik olanları geçersiz kılabilirsiniz. Aşağıdaki örnekte, Unicode karakterlerini desteklemek için NOCASE harmanlamasının geçersiz kılınması gösterilmektedir. [Tam örnek kod](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) GitHub ' da kullanılabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like işleci

SQLite içindeki LIKE işleci harmanlamaları dikkate almaz. Varsayılan uygulama, NOCASE harmanlamasıyla aynı semantiğe sahiptir. Yalnızca A-Z ASCII karakterleri için büyük/küçük harfe duyarsızdır.

Aşağıdaki pragma ifadesini kullanarak LIKE işlecinin büyük küçük harfe duyarlı olmasını kolayca sağlayabilirsiniz:

```sql
PRAGMA case_sensitive_like = 0
```

LIKE işlecinin uygulanmasını geçersiz kılma hakkında ayrıntılar için [Kullanıcı tanımlı işlevlere](user-defined-functions.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Kullanıcı tanımlı işlevler](user-defined-functions.md)
* [SQL Söz Dizimi](https://www.sqlite.org/lang.html)
