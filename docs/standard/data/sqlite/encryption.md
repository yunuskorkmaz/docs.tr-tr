---
title: Şifreleme
ms.date: 12/13/2019
description: Veritabanı dosyanızı şifrelemeyi öğrenin.
ms.openlocfilehash: ccdd4b6b8642b3cde1c2667c9ca432a9b0ef21f2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447267"
---
# <a name="encryption"></a>Şifreleme

SQLite, veritabanı dosyalarını varsayılan olarak şifrelemeyi desteklemez. Bunun yerine, bkz. SQLite 'un değiştirilmiş bir sürümünü [görmeniz](https://www.hwaci.com/sw/sqlite/see.html)gerekir, örneğin, [sqlcipher](https://www.zetetic.net/sqlcipher/), [Sqlitecrypt](http://www.sqlite-crypt.com/)veya [wxSQLite3](https://utelle.github.io/wxsqlite3). Bu makalede, desteklenmeyen ve açık kaynaklı bir SQLCipher derlemesi kullanılması gösterilmektedir, ancak bu bilgiler genellikle aynı kalıbı izledikleri için diğer çözümler için de geçerlidir.

## <a name="installation"></a>Yükleme

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

Şifreleme için farklı bir yerel kitaplık kullanma hakkında daha fazla bilgi için bkz. [özel SQLite sürümleri](custom-versions.md).

## <a name="specify-the-key"></a>Anahtarı belirtin

Şifrelemeyi etkinleştirmek için `Password` bağlantı dizesi anahtar sözcüğünü kullanarak anahtarı belirtin. Kullanıcı girişinden değer eklemek veya güncelleştirmek ve bağlantı dizesi ekleme saldırılarına engel olmak için <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> kullanın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a>Veritabanını yeniden anahtarlama

Bir veritabanının şifreleme anahtarını değiştirmek istiyorsanız, bir `PRAGMA rekey` ifadesini yayınlayın. Veritabanının şifresini çözmek için `NULL`belirtin.

Ne yazık ki, SQLite `PRAGMA` deyimlerdeki parametreleri desteklemez. Bunun yerine, SQL ekleme işlemini engellemek için `quote()` işlevini kullanın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
