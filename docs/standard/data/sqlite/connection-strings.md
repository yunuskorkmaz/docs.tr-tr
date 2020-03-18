---
title: Bağlantı dizeleri
ms.date: 12/13/2019
description: Desteklenen anahtar kelimeler ve bağlantı dizeleri değerleri.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400451"
---
# <a name="connection-strings"></a><span data-ttu-id="05947-103">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="05947-103">Connection strings</span></span>

<span data-ttu-id="05947-104">Veritabanına nasıl bağlanılmayı belirtmek için bir bağlantı dizesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05947-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="05947-105">Microsoft.Data.Sqlite'deki bağlantı dizeleri, standart [ADO.NET sözdizimini](../../../framework/data/adonet/connection-strings.md) yarı sütunlu ayrılmış anahtar kelimeler ve değerler listesi olarak izler.</span><span class="sxs-lookup"><span data-stu-id="05947-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="05947-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="05947-106">Keywords</span></span>

<span data-ttu-id="05947-107">Aşağıdaki bağlantı dize anahtar kelimeleri Microsoft.Data.Sqlite ile kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="05947-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="05947-108">Veri kaynağı</span><span class="sxs-lookup"><span data-stu-id="05947-108">Data source</span></span>

<span data-ttu-id="05947-109">Veritabanı dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="05947-109">The path to the database file.</span></span> <span data-ttu-id="05947-110">*DataSource* (boşluk olmadan) ve *Dosya Adı* bu anahtar kelimenin diğer adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="05947-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="05947-111">SQLite, yollara geçerli çalışma dizinine göre davranır.</span><span class="sxs-lookup"><span data-stu-id="05947-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="05947-112">Mutlak yollar da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="05947-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="05947-113">**Boşsa,** SQLite bağlantı kapatıldığında silinen geçici bir disk veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05947-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="05947-114">, `:memory:`bellek içi veritabanı kullanılırsa.</span><span class="sxs-lookup"><span data-stu-id="05947-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="05947-115">Daha fazla bilgi için Bellek [İçi veritabanlarına](in-memory-databases.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="05947-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="05947-116">Değiştirme dizesiyle `|DataDirectory|` başlayan yollar, göreli yollarla aynı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="05947-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="05947-117">Ayarlanırsa, yollar DataDirectory uygulama etki alanı özelliği değerine göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="05947-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="05947-118">Bu anahtar kelime aynı zamanda [URI Dosya adlarını](https://www.sqlite.org/uri.html)da destekler.</span><span class="sxs-lookup"><span data-stu-id="05947-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="05947-119">Mod</span><span class="sxs-lookup"><span data-stu-id="05947-119">Mode</span></span>

<span data-ttu-id="05947-120">Bağlantı modu.</span><span class="sxs-lookup"><span data-stu-id="05947-120">The connection mode.</span></span>

| <span data-ttu-id="05947-121">Değer</span><span class="sxs-lookup"><span data-stu-id="05947-121">Value</span></span>           | <span data-ttu-id="05947-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05947-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="05947-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="05947-123">ReadWriteCreate</span></span> | <span data-ttu-id="05947-124">Okuma ve yazma için veritabanını açar ve yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05947-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="05947-125">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05947-125">This is the default.</span></span> |
| <span data-ttu-id="05947-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="05947-126">ReadWrite</span></span>       | <span data-ttu-id="05947-127">Okuma ve yazma için veritabanını açar.</span><span class="sxs-lookup"><span data-stu-id="05947-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="05947-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="05947-128">ReadOnly</span></span>        | <span data-ttu-id="05947-129">Veritabanını salt okunur modunda açar.</span><span class="sxs-lookup"><span data-stu-id="05947-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="05947-130">Bellek</span><span class="sxs-lookup"><span data-stu-id="05947-130">Memory</span></span>          | <span data-ttu-id="05947-131">Bellek içi bir veritabanı açar.</span><span class="sxs-lookup"><span data-stu-id="05947-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="05947-132">Önbellek</span><span class="sxs-lookup"><span data-stu-id="05947-132">Cache</span></span>

<span data-ttu-id="05947-133">Bağlantı tarafından kullanılan önbelleğe alma modu.</span><span class="sxs-lookup"><span data-stu-id="05947-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="05947-134">Değer</span><span class="sxs-lookup"><span data-stu-id="05947-134">Value</span></span>   | <span data-ttu-id="05947-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05947-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="05947-136">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="05947-136">Default</span></span> | <span data-ttu-id="05947-137">Temel SQLite kitaplığın varsayılan modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="05947-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="05947-138">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05947-138">This is the default.</span></span>                   |
| <span data-ttu-id="05947-139">Özel</span><span class="sxs-lookup"><span data-stu-id="05947-139">Private</span></span> | <span data-ttu-id="05947-140">Her bağlantı özel bir önbellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="05947-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="05947-141">Paylaşımlı</span><span class="sxs-lookup"><span data-stu-id="05947-141">Shared</span></span>  | <span data-ttu-id="05947-142">Bağlantılar önbelleği paylaşır.</span><span class="sxs-lookup"><span data-stu-id="05947-142">Connections share a cache.</span></span> <span data-ttu-id="05947-143">Bu mod, işlem ve tablo kilitleme davranışını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="05947-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="05947-144">Parola</span><span class="sxs-lookup"><span data-stu-id="05947-144">Password</span></span>

<span data-ttu-id="05947-145">Şifreleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="05947-145">The encryption key.</span></span> <span data-ttu-id="05947-146">Belirtildiğinde, `PRAGMA key` bağlantıyı açtıktan hemen sonra gönderilir.</span><span class="sxs-lookup"><span data-stu-id="05947-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="05947-147">Şifreleme yerel SQLite kitaplığı tarafından desteklenmediği zaman parolanın hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="05947-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="05947-148">Yabancı Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="05947-148">Foreign Keys</span></span>

<span data-ttu-id="05947-149">Yabancı anahtar kısıtlamalarının etkinleştirilip etkinleştirilemeyeceğini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="05947-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="05947-150">Değer</span><span class="sxs-lookup"><span data-stu-id="05947-150">Value</span></span>   | <span data-ttu-id="05947-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05947-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="05947-152">True</span><span class="sxs-lookup"><span data-stu-id="05947-152">True</span></span>    | <span data-ttu-id="05947-153">Bağlantıyı `PRAGMA foreign_keys = 1` açtıktan hemen sonra gönderir.</span><span class="sxs-lookup"><span data-stu-id="05947-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="05947-154">False</span><span class="sxs-lookup"><span data-stu-id="05947-154">False</span></span>   | <span data-ttu-id="05947-155">Bağlantıyı `PRAGMA foreign_keys = 0` açtıktan hemen sonra gönderir.</span><span class="sxs-lookup"><span data-stu-id="05947-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="05947-156">(boş)</span><span class="sxs-lookup"><span data-stu-id="05947-156">(empty)</span></span> | <span data-ttu-id="05947-157">`PRAGMA foreign_keys`Göndermiyor.</span><span class="sxs-lookup"><span data-stu-id="05947-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="05947-158">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05947-158">This is the default.</span></span> |

<span data-ttu-id="05947-159">yerel SQLite kitaplığını derlemek için SQLITE_DEFAULT_FOREIGN_KEYS e_sqlite3'da olduğu gibi yabancı anahtarları etkinleştirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="05947-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="05947-160">Özyinelemeli tetikleyiciler</span><span class="sxs-lookup"><span data-stu-id="05947-160">Recursive triggers</span></span>

<span data-ttu-id="05947-161">Özyinelemeli tetikleyicileri etkinleştirip etkinleştirmeyeceğini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="05947-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="05947-162">Değer</span><span class="sxs-lookup"><span data-stu-id="05947-162">Value</span></span> | <span data-ttu-id="05947-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05947-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="05947-164">True</span><span class="sxs-lookup"><span data-stu-id="05947-164">True</span></span>  | <span data-ttu-id="05947-165">Bağlantıyı `PRAGMA recursive_triggers` açtıktan hemen sonra gönderir.</span><span class="sxs-lookup"><span data-stu-id="05947-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="05947-166">False</span><span class="sxs-lookup"><span data-stu-id="05947-166">False</span></span> | <span data-ttu-id="05947-167">`PRAGMA recursive_triggers`Göndermiyor.</span><span class="sxs-lookup"><span data-stu-id="05947-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="05947-168">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05947-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="05947-169">Bağlantı dize oluşturucu</span><span class="sxs-lookup"><span data-stu-id="05947-169">Connection string builder</span></span>

<span data-ttu-id="05947-170">Bağlantı dizeleri oluşturmanın güçlü bir şekilde yazılmış bir yolu olarak kullanabilirsiniz. <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder></span><span class="sxs-lookup"><span data-stu-id="05947-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="05947-171">Ayrıca bağlantı string enjeksiyon saldırılarını önlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05947-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="05947-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="05947-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="05947-173">Temel</span><span class="sxs-lookup"><span data-stu-id="05947-173">Basic</span></span>

<span data-ttu-id="05947-174">Geliştirilmiş eşzamanlılık için paylaşılan önbelleği olan temel bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="05947-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="05947-175">Şifreli</span><span class="sxs-lookup"><span data-stu-id="05947-175">Encrypted</span></span>

<span data-ttu-id="05947-176">Şifreli bir veritabanı.</span><span class="sxs-lookup"><span data-stu-id="05947-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="05947-177">Salt okunur</span><span class="sxs-lookup"><span data-stu-id="05947-177">Read-only</span></span>

<span data-ttu-id="05947-178">Uygulama tarafından değiştirilemeyen salt okunur veritabanı.</span><span class="sxs-lookup"><span data-stu-id="05947-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="05947-179">Bellek içi</span><span class="sxs-lookup"><span data-stu-id="05947-179">In-memory</span></span>

<span data-ttu-id="05947-180">Özel, hafıza içi bir veritabanı.</span><span class="sxs-lookup"><span data-stu-id="05947-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="05947-181">Bellekte sharable</span><span class="sxs-lookup"><span data-stu-id="05947-181">Sharable in-memory</span></span>

<span data-ttu-id="05947-182">*Sharable*adıyla tanımlanan sharable, in-memory veritabanı.</span><span class="sxs-lookup"><span data-stu-id="05947-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="05947-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05947-183">See also</span></span>

* [<span data-ttu-id="05947-184">ADO.NET Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="05947-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="05947-185">Bellek veritabanları</span><span class="sxs-lookup"><span data-stu-id="05947-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="05947-186">İşlemler</span><span class="sxs-lookup"><span data-stu-id="05947-186">Transactions</span></span>](transactions.md)
