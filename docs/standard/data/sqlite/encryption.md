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
# <a name="encryption"></a><span data-ttu-id="d26d3-103">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="d26d3-103">Encryption</span></span>

<span data-ttu-id="d26d3-104">SQLite, veritabanı dosyalarını varsayılan olarak şifrelemeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d26d3-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="d26d3-105">Bunun yerine, bkz. SQLite 'un değiştirilmiş bir sürümünü [görmeniz](https://www.hwaci.com/sw/sqlite/see.html)gerekir, örneğin, [sqlcipher](https://www.zetetic.net/sqlcipher/), [Sqlitecrypt](http://www.sqlite-crypt.com/)veya [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="d26d3-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="d26d3-106">Bu makalede, desteklenmeyen ve açık kaynaklı bir SQLCipher derlemesi kullanılması gösterilmektedir, ancak bu bilgiler genellikle aynı kalıbı izledikleri için diğer çözümler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d26d3-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="d26d3-107">Yükleme</span><span class="sxs-lookup"><span data-stu-id="d26d3-107">Installation</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="d26d3-108">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="d26d3-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="d26d3-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d26d3-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="d26d3-110">Şifreleme için farklı bir yerel kitaplık kullanma hakkında daha fazla bilgi için bkz. [özel SQLite sürümleri](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="d26d3-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="d26d3-111">Anahtarı belirtin</span><span class="sxs-lookup"><span data-stu-id="d26d3-111">Specify the key</span></span>

<span data-ttu-id="d26d3-112">Yeni bir veritabanında şifrelemeyi etkinleştirmek için `Password` bağlantı dizesi anahtar sözcüğünü kullanarak anahtarı belirtin.</span><span class="sxs-lookup"><span data-stu-id="d26d3-112">To enable encryption on a new database, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="d26d3-113"><xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>Kullanıcı girişinden değer eklemek veya güncelleştirmek için kullanın ve bağlantı dizesi ekleme saldırılarına karşı önleyin.</span><span class="sxs-lookup"><span data-stu-id="d26d3-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> <span data-ttu-id="d26d3-114">Mevcut veritabanlarını şifreleme ve şifrelerini çözme yöntemi, kullandığınız çözüme bağlı olarak değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="d26d3-114">The method for encrypting and decrypting existing databases varies depending on which solution you're using.</span></span> <span data-ttu-id="d26d3-115">Örneğin, `sqlcipher_export()` SQLCipher üzerinde işlevini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d26d3-115">For example, you need to use the `sqlcipher_export()` function on SQLCipher.</span></span> <span data-ttu-id="d26d3-116">Ayrıntılar için çözümünüzün belgelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d26d3-116">Check your solution's documentation for details.</span></span>

## <a name="rekeying-the-database"></a><span data-ttu-id="d26d3-117">Veritabanını yeniden anahtarlama</span><span class="sxs-lookup"><span data-stu-id="d26d3-117">Rekeying the database</span></span>

<span data-ttu-id="d26d3-118">Şifrelenmiş bir veritabanının anahtarını değiştirmek istiyorsanız, bir `PRAGMA rekey` ifade yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="d26d3-118">If you want to change the key of an encrypted database, issue a `PRAGMA rekey` statement.</span></span>

<span data-ttu-id="d26d3-119">Ne yazık ki, SQLite `PRAGMA` deyimlerdeki parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d26d3-119">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="d26d3-120">Bunun yerine, `quote()` SQL ekleme işlemini engellemek için işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d26d3-120">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
