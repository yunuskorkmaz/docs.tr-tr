---
title: Bağlantı dizeleri
ms.date: 12/08/2020
description: Desteklenen anahtar sözcükler ve bağlantı dizelerinin değerleri.
ms.openlocfilehash: 35283664c4ac3985d4f517fde77644ab2a891120
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110747"
---
# <a name="connection-strings"></a><span data-ttu-id="c45a9-103">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="c45a9-103">Connection strings</span></span>

<span data-ttu-id="c45a9-104">Bir bağlantı dizesi, veritabanına nasıl bağlanılacağını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="c45a9-105">Microsoft. Data. SQLite içindeki bağlantı dizeleri standart [ADO.net söz dizimini](../../../framework/data/adonet/connection-strings.md) , noktalı virgülle ayrılmış bir anahtar sözcük ve değer listesi olarak izler.</span><span class="sxs-lookup"><span data-stu-id="c45a9-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="c45a9-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c45a9-106">Keywords</span></span>

<span data-ttu-id="c45a9-107">Aşağıdaki bağlantı dizesi anahtar sözcükleri Microsoft. Data. SQLite ile kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c45a9-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="c45a9-108">Veri kaynağı</span><span class="sxs-lookup"><span data-stu-id="c45a9-108">Data source</span></span>

<span data-ttu-id="c45a9-109">Veritabanı dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="c45a9-109">The path to the database file.</span></span> <span data-ttu-id="c45a9-110">*Veri kaynağı* (boşluk olmadan) ve *dosya adı* bu anahtar sözcüğünün diğer adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="c45a9-111">SQLite, yolları geçerli çalışma dizinine göre değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="c45a9-112">Mutlak yollar da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="c45a9-113">**Boşsa**, SQLite bağlantı kapalıyken silinen geçici bir disk üzerinde veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c45a9-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="c45a9-114">İse `:memory:` , bellek içi bir veritabanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="c45a9-115">Daha fazla bilgi için bkz. [bellek içi veritabanları](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c45a9-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="c45a9-116">`|DataDirectory|`Değiştirme dizesiyle başlayan yollar göreli yollarla aynı şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="c45a9-117">Ayarlanırsa, yollar DataDirectory uygulama etki alanı özellik değerine göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="c45a9-118">Bu anahtar sözcük ayrıca [URI dosya adlarını](https://www.sqlite.org/uri.html)destekler.</span><span class="sxs-lookup"><span data-stu-id="c45a9-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="c45a9-119">Mod</span><span class="sxs-lookup"><span data-stu-id="c45a9-119">Mode</span></span>

<span data-ttu-id="c45a9-120">Bağlantı modu.</span><span class="sxs-lookup"><span data-stu-id="c45a9-120">The connection mode.</span></span>

| <span data-ttu-id="c45a9-121">Değer</span><span class="sxs-lookup"><span data-stu-id="c45a9-121">Value</span></span>           | <span data-ttu-id="c45a9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c45a9-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c45a9-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="c45a9-123">ReadWriteCreate</span></span> | <span data-ttu-id="c45a9-124">Veritabanını okumak ve yazmak için açar ve yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c45a9-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="c45a9-125">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-125">This is the default.</span></span> |
| <span data-ttu-id="c45a9-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="c45a9-126">ReadWrite</span></span>       | <span data-ttu-id="c45a9-127">Veritabanını okumak ve yazmak için açar.</span><span class="sxs-lookup"><span data-stu-id="c45a9-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="c45a9-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c45a9-128">ReadOnly</span></span>        | <span data-ttu-id="c45a9-129">Veritabanını salt okuma modunda açar.</span><span class="sxs-lookup"><span data-stu-id="c45a9-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="c45a9-130">Bellek</span><span class="sxs-lookup"><span data-stu-id="c45a9-130">Memory</span></span>          | <span data-ttu-id="c45a9-131">Bellek içi veritabanı açar.</span><span class="sxs-lookup"><span data-stu-id="c45a9-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="c45a9-132">Önbellek</span><span class="sxs-lookup"><span data-stu-id="c45a9-132">Cache</span></span>

<span data-ttu-id="c45a9-133">Bağlantı tarafından kullanılan önbelleğe alma modu.</span><span class="sxs-lookup"><span data-stu-id="c45a9-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="c45a9-134">Değer</span><span class="sxs-lookup"><span data-stu-id="c45a9-134">Value</span></span>   | <span data-ttu-id="c45a9-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c45a9-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c45a9-136">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="c45a9-136">Default</span></span> | <span data-ttu-id="c45a9-137">Temel alınan SQLite kitaplığının varsayılan modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="c45a9-138">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-138">This is the default.</span></span>                   |
| <span data-ttu-id="c45a9-139">Özel</span><span class="sxs-lookup"><span data-stu-id="c45a9-139">Private</span></span> | <span data-ttu-id="c45a9-140">Her bağlantı özel bir önbellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="c45a9-141">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="c45a9-141">Shared</span></span>  | <span data-ttu-id="c45a9-142">Bağlantılar bir önbelleği paylaşır.</span><span class="sxs-lookup"><span data-stu-id="c45a9-142">Connections share a cache.</span></span> <span data-ttu-id="c45a9-143">Bu mod işlem ve tablo kilitleme davranışını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="c45a9-144">Parola</span><span class="sxs-lookup"><span data-stu-id="c45a9-144">Password</span></span>

<span data-ttu-id="c45a9-145">Şifreleme anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c45a9-145">The encryption key.</span></span> <span data-ttu-id="c45a9-146">Belirtildiğinde, `PRAGMA key` bağlantı açıldıktan hemen sonra gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="c45a9-147">Şifreleme yerel SQLite kitaplığı tarafından desteklenmiyorsa parolanın hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c45a9-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

> [!NOTE]
> <span data-ttu-id="c45a9-148">Password anahtar sözcüğü 3,0 sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-148">The Password keyword was added in version 3.0.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="c45a9-149">Yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="c45a9-149">Foreign Keys</span></span>

<span data-ttu-id="c45a9-150">Yabancı anahtar kısıtlamalarının etkinleştirilip etkinleştirilmeyeceğini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c45a9-150">A value indicating whether to enable foreign key constraints.</span></span>

> [!NOTE]
> <span data-ttu-id="c45a9-151">Yabancı anahtarlar anahtar sözcüğü 3,0 sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-151">The Foreign Keys keyword was added in version 3.0.</span></span>

| <span data-ttu-id="c45a9-152">Değer</span><span class="sxs-lookup"><span data-stu-id="c45a9-152">Value</span></span>   | <span data-ttu-id="c45a9-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c45a9-153">Description</span></span>
| ------- | --- |
| <span data-ttu-id="c45a9-154">Doğru</span><span class="sxs-lookup"><span data-stu-id="c45a9-154">True</span></span>    | <span data-ttu-id="c45a9-155">`PRAGMA foreign_keys = 1`Bağlantıyı açtıktan hemen sonra gönderir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-155">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="c45a9-156">Yanlış</span><span class="sxs-lookup"><span data-stu-id="c45a9-156">False</span></span>   | <span data-ttu-id="c45a9-157">`PRAGMA foreign_keys = 0`Bağlantıyı açtıktan hemen sonra gönderir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-157">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="c45a9-158">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="c45a9-158">(empty)</span></span> | <span data-ttu-id="c45a9-159">Göndermez `PRAGMA foreign_keys` .</span><span class="sxs-lookup"><span data-stu-id="c45a9-159">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="c45a9-160">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-160">This is the default.</span></span> |

<span data-ttu-id="c45a9-161">E_sqlite3 gibi, yerel SQLite kitaplığı derlemek için SQLITE_DEFAULT_FOREIGN_KEYS kullanıldığında yabancı anahtarların etkinleştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c45a9-161">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="c45a9-162">Özyinelemeli Tetikleyiciler</span><span class="sxs-lookup"><span data-stu-id="c45a9-162">Recursive triggers</span></span>

<span data-ttu-id="c45a9-163">Özyinelemeli tetikleyicilerin etkinleştirilip etkinleştirilmeyeceğini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c45a9-163">A value that indicates whether to enable recursive triggers.</span></span>

> [!NOTE]
> <span data-ttu-id="c45a9-164">Özyinelemeli Tetikleyiciler anahtar sözcüğü 3,0 sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-164">The Recursive Triggers keyword was added in version 3.0.</span></span>

| <span data-ttu-id="c45a9-165">Değer</span><span class="sxs-lookup"><span data-stu-id="c45a9-165">Value</span></span> | <span data-ttu-id="c45a9-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c45a9-166">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="c45a9-167">Doğru</span><span class="sxs-lookup"><span data-stu-id="c45a9-167">True</span></span>  | <span data-ttu-id="c45a9-168">`PRAGMA recursive_triggers`Bağlantıyı açtıktan hemen sonra gönderir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-168">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="c45a9-169">Yanlış</span><span class="sxs-lookup"><span data-stu-id="c45a9-169">False</span></span> | <span data-ttu-id="c45a9-170">Göndermez `PRAGMA recursive_triggers` .</span><span class="sxs-lookup"><span data-stu-id="c45a9-170">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="c45a9-171">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-171">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="c45a9-172">Bağlantı dizesi Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="c45a9-172">Connection string builder</span></span>

<span data-ttu-id="c45a9-173"><xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>Bağlantı dizelerini oluşturmak için türü kesin belirlenmiş bir yöntem olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c45a9-173">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="c45a9-174">Bağlantı dizesi ekleme saldırılarını engellemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c45a9-174">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="c45a9-175">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c45a9-175">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="c45a9-176">Temel</span><span class="sxs-lookup"><span data-stu-id="c45a9-176">Basic</span></span>

<span data-ttu-id="c45a9-177">İyileştirilmiş eşzamanlılık için paylaşılan önbelleği olan temel bir bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="c45a9-177">A basic connection string with a shared cache for improved concurrency.</span></span>

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="c45a9-178">Şifreli</span><span class="sxs-lookup"><span data-stu-id="c45a9-178">Encrypted</span></span>

<span data-ttu-id="c45a9-179">Şifrelenmiş bir veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c45a9-179">An encrypted database.</span></span>

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="c45a9-180">Salt okunur</span><span class="sxs-lookup"><span data-stu-id="c45a9-180">Read-only</span></span>

<span data-ttu-id="c45a9-181">Uygulama tarafından değiştirilemeyen salt biçimli bir veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c45a9-181">A read-only database that cannot be modified by the app.</span></span>

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="c45a9-182">Bellek içi</span><span class="sxs-lookup"><span data-stu-id="c45a9-182">In-memory</span></span>

<span data-ttu-id="c45a9-183">Özel, bellek içi veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c45a9-183">A private, in-memory database.</span></span>

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="c45a9-184">Paylaşılabilir bellek içi</span><span class="sxs-lookup"><span data-stu-id="c45a9-184">Sharable in-memory</span></span>

<span data-ttu-id="c45a9-185">*Paylaşılabilir* adıyla tanımlanan paylaşılabilir, bellek içi veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c45a9-185">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="c45a9-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c45a9-186">See also</span></span>

* [<span data-ttu-id="c45a9-187">ADO.NET içinde bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="c45a9-187">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="c45a9-188">Bellek içi veritabanları</span><span class="sxs-lookup"><span data-stu-id="c45a9-188">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="c45a9-189">İşlemler</span><span class="sxs-lookup"><span data-stu-id="c45a9-189">Transactions</span></span>](transactions.md)
