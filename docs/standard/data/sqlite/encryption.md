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
# <a name="encryption"></a><span data-ttu-id="f1013-103">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="f1013-103">Encryption</span></span>

<span data-ttu-id="f1013-104">SQLite, veritabanı dosyalarını varsayılan olarak şifrelemeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f1013-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="f1013-105">Bunun yerine, bkz. SQLite 'un değiştirilmiş bir sürümünü [görmeniz](https://www.hwaci.com/sw/sqlite/see.html)gerekir, örneğin, [sqlcipher](https://www.zetetic.net/sqlcipher/), [Sqlitecrypt](http://www.sqlite-crypt.com/)veya [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="f1013-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="f1013-106">Bu makalede, desteklenmeyen ve açık kaynaklı bir SQLCipher derlemesi kullanılması gösterilmektedir, ancak bu bilgiler genellikle aynı kalıbı izledikleri için diğer çözümler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1013-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="f1013-107">Yükleme</span><span class="sxs-lookup"><span data-stu-id="f1013-107">Installation</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="f1013-108">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="f1013-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="f1013-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f1013-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="f1013-110">Şifreleme için farklı bir yerel kitaplık kullanma hakkında daha fazla bilgi için bkz. [özel SQLite sürümleri](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f1013-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="f1013-111">Anahtarı belirtin</span><span class="sxs-lookup"><span data-stu-id="f1013-111">Specify the key</span></span>

<span data-ttu-id="f1013-112">Şifrelemeyi etkinleştirmek için `Password` bağlantı dizesi anahtar sözcüğünü kullanarak anahtarı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1013-112">To enable encryption, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="f1013-113">Kullanıcı <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> girişinden değer eklemek veya güncelleştirmek için kullanın ve bağlantı dizesi ekleme saldırılarına karşı önleyin.</span><span class="sxs-lookup"><span data-stu-id="f1013-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a><span data-ttu-id="f1013-114">Veritabanını yeniden anahtarlama</span><span class="sxs-lookup"><span data-stu-id="f1013-114">Rekeying the database</span></span>

<span data-ttu-id="f1013-115">Bir veritabanının şifreleme anahtarını değiştirmek istiyorsanız, bir `PRAGMA rekey` ifade yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="f1013-115">If you want to change the encryption key of a database, issue a `PRAGMA rekey` statement.</span></span> <span data-ttu-id="f1013-116">Veritabanının şifresini çözmek için öğesini belirtin `NULL`.</span><span class="sxs-lookup"><span data-stu-id="f1013-116">To decrypt the database, specify `NULL`.</span></span>

<span data-ttu-id="f1013-117">Ne yazık ki, SQLite deyimlerdeki `PRAGMA` parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f1013-117">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="f1013-118">Bunun yerine, SQL `quote()` ekleme işlemini engellemek için işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1013-118">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
