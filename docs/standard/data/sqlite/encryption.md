---
title: Şifreleme
ms.date: 09/08/2020
description: Veritabanı dosyanızı şifrelemeyi öğrenin.
ms.openlocfilehash: 1b33e1510a269aba87caba2cd39faab33791aa55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203416"
---
# <a name="encryption"></a>Şifreleme

SQLite, veritabanı dosyalarını varsayılan olarak şifrelemeyi desteklemez. Bunun yerine, bkz. SQLite 'un değiştirilmiş bir sürümünü [görmeniz](https://www.hwaci.com/sw/sqlite/see.html)gerekir, örneğin, [sqlcipher](https://www.zetetic.net/sqlcipher/), [Sqlitecrypt](http://www.sqlite-crypt.com/)veya [wxSQLite3](https://utelle.github.io/wxsqlite3). Bu makalede, desteklenmeyen ve açık kaynaklı bir SQLCipher derlemesi kullanılması gösterilmektedir, ancak bu bilgiler genellikle aynı kalıbı izledikleri için diğer çözümler için de geçerlidir.

## <a name="installation"></a>Yükleme

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

Şifreleme için farklı bir yerel kitaplık kullanma hakkında daha fazla bilgi için bkz. [özel SQLite sürümleri](custom-versions.md).

## <a name="specify-the-key"></a>Anahtarı belirtin

Yeni bir veritabanında şifrelemeyi etkinleştirmek için `Password` bağlantı dizesi anahtar sözcüğünü kullanarak anahtarı belirtin. <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>Kullanıcı girişinden değer eklemek veya güncelleştirmek için kullanın ve bağlantı dizesi ekleme saldırılarına karşı önleyin.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> Mevcut veritabanlarını şifreleme ve şifrelerini çözme yöntemi, kullandığınız çözüme bağlı olarak değişiklik gösterir. Örneğin, `sqlcipher_export()` SQLCipher üzerinde işlevini kullanmanız gerekir. Ayrıntılar için çözümünüzün belgelerini denetleyin.

## <a name="rekeying-the-database"></a>Veritabanını yeniden anahtarlama

Şifrelenmiş bir veritabanının anahtarını değiştirmek istiyorsanız, bir `PRAGMA rekey` ifade yayınlayın.

Ne yazık ki, SQLite `PRAGMA` deyimlerdeki parametreleri desteklemez. Bunun yerine, `quote()` SQL ekleme işlemini engellemek için işlevini kullanın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
