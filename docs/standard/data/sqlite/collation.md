---
title: Harmanlama
ms.date: 12/13/2019
description: Özel bir harmanlama dizisi oluşturmayı öğrenin.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242978"
---
# <a name="collation"></a>Harmanlama

Dizileri harmanlama, düzen ve eşitliği belirlemek için TEXT değerlerini karşılaştırırken SQLite tarafından kullanılır. SQL sorgularında sütun oluştururken veya işlem başına kullanırken hangi harmanlamanın kullanılacağını belirtebilirsiniz. SQLite varsayılan olarak üç harmanlama dizisi içerir.

| Harmanlama | Açıklama                               |
| --------- | ----------------------------------------- |
| RTRIM     | Sondaki beyaz boşluğu yok sayar               |
| NOCASE    | ASCII karakterleri a-z için büyük/küçük harf duyarsız |
| Ikili    | Duyarlı. Baytları doğrudan karşılaştırır   |

## <a name="custom-collation"></a>Özel harmanlama

Ayrıca kendi harmanlama dizilerinizi tanımlayabilir veya yerleşik sekanları <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>kullanarak geçersiz kılabilirsiniz. Aşağıdaki örnek, Unicode karakterlerini desteklemek için NOCASE harmanlama geçersiz kılınan gösterir. [Tam örnek kodu](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) GitHub'da kullanılabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Operatör gibi

SQLite LIKE operatör collations onurlandırmaz. Varsayılan uygulama NOCASE harmanlama aynı semantik vardır. A'dan Z'ye KADAR ASCII karakterleri için sadece büyük bir duyarsızlık.

Aşağıdaki pragma deyimini kullanarak LIKE işleci kılıfını kolayca hassas hale getirebilirsiniz:

```sql
PRAGMA case_sensitive_like = 1
```

LIKE işlecinin uygulanmasını geçersiz kılmayla ilgili ayrıntılar için [Kullanıcı tanımlı işlevlere](user-defined-functions.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Kullanıcı tanımlı işlevler](user-defined-functions.md)
* [SQL Söz Dizimi](https://www.sqlite.org/lang.html)
