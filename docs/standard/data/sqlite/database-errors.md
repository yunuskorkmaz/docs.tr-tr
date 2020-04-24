---
title: Veritabanı hataları
ms.date: 12/13/2019
description: Veritabanı hatalarının ve deponun kitaplık tarafından nasıl işlendiğini açıklar.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447274"
---
# <a name="database-errors"></a><span data-ttu-id="87f46-103">Veritabanı hataları</span><span class="sxs-lookup"><span data-stu-id="87f46-103">Database errors</span></span>

<span data-ttu-id="87f46-104"><xref:Microsoft.Data.Sqlite.SqliteException>bir SQLite hatası ile karşılaşıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87f46-104"><xref:Microsoft.Data.Sqlite.SqliteException> is thrown when a SQLite error is encountered.</span></span> <span data-ttu-id="87f46-105">İleti SQLite tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="87f46-105">The message is provided by SQLite.</span></span> <span data-ttu-id="87f46-106">Ve `SqliteErrorCode` `SqliteExtendedErrorCode` özellikleri, hatanın SQLite [sonuç kodunu](https://www.sqlite.org/rescode.html) içerir.</span><span class="sxs-lookup"><span data-stu-id="87f46-106">The `SqliteErrorCode` and `SqliteExtendedErrorCode` properties contain the SQLite [result code](https://www.sqlite.org/rescode.html) of the error.</span></span>

<span data-ttu-id="87f46-107">Microsoft. Data. SQLite yerel SQLite kitaplığı ile etkileşime geçtiğinde hatalarla karşılaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="87f46-107">Errors may be encountered any time the Microsoft.Data.Sqlite interacts with the native SQLite library.</span></span> <span data-ttu-id="87f46-108">Aşağıdaki listede, hataların gerçekleşebileceği yaygın senaryolar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="87f46-108">The following list shows the common scenarios where errors can occur:</span></span>

* <span data-ttu-id="87f46-109">Bir bağlantı açılıyor.</span><span class="sxs-lookup"><span data-stu-id="87f46-109">Opening a connection.</span></span>
* <span data-ttu-id="87f46-110">İşlem başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="87f46-110">Beginning a transaction.</span></span>
* <span data-ttu-id="87f46-111">Bir komut yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="87f46-111">Executing a command.</span></span>
* <span data-ttu-id="87f46-112">Çağrılıyor <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span><span class="sxs-lookup"><span data-stu-id="87f46-112">Calling <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span></span>

<span data-ttu-id="87f46-113">Uygulamanızın bu hataları nasıl işleyeceğini dikkatle düşünün.</span><span class="sxs-lookup"><span data-stu-id="87f46-113">Consider carefully how your app will handle these errors.</span></span>

## <a name="locking-retries-and-timeouts"></a><span data-ttu-id="87f46-114">Kilitleme, yeniden denemeler ve zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="87f46-114">Locking, retries, and timeouts</span></span>

<span data-ttu-id="87f46-115">SQLite, tabloları ve veritabanı dosyalarını kilitlemek için gelir.</span><span class="sxs-lookup"><span data-stu-id="87f46-115">SQLite is aggressive when it comes to locking tables and database files.</span></span> <span data-ttu-id="87f46-116">Uygulamanız eşzamanlı veritabanı erişimi sağladığından, büyük olasılıkla meşgul ve kilitli hatalarıyla karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="87f46-116">If your app enables any concurrent database access, you'll likely encounter busy and locked errors.</span></span> <span data-ttu-id="87f46-117">[Paylaşılan bir önbellek](connection-strings.md#cache) ve [yazma öncesi günlük](async.md)kullanarak birçok hatayı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87f46-117">You can mitigate many errors by using a [shared cache](connection-strings.md#cache) and [write-ahead logging](async.md).</span></span>

<span data-ttu-id="87f46-118">Microsoft. Data. SQLite, meşgul veya kilitli bir hatayla karşılaştığında otomatik olarak yeniden dener veya komut zaman aşımına ulaşılacaktır.</span><span class="sxs-lookup"><span data-stu-id="87f46-118">Whenever Microsoft.Data.Sqlite encounters a busy or locked error, it will automatically retry until it succeeds or the command timeout is reached.</span></span>

<span data-ttu-id="87f46-119">Komutunu ayarlayarak <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>komut zaman aşımını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87f46-119">You can increase the timeout of command by setting <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span></span> <span data-ttu-id="87f46-120">Varsayılan zaman aşımı 30 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="87f46-120">The default timeout is 30 seconds.</span></span> <span data-ttu-id="87f46-121">Bir değeri zaman `0` aşımı değildir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87f46-121">A value of `0` means no timeout.</span></span>

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

<span data-ttu-id="87f46-122">Microsoft. Data. SQLite bazen örtük bir komut nesnesi oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87f46-122">Microsoft.Data.Sqlite sometimes needs to create an implicit command object.</span></span> <span data-ttu-id="87f46-123">Örneğin, BeginTransaction sırasında.</span><span class="sxs-lookup"><span data-stu-id="87f46-123">For example, during BeginTransaction.</span></span> <span data-ttu-id="87f46-124">Bu komutlara ilişkin zaman aşımını ayarlamak için kullanın <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="87f46-124">To set the timeout for these commands, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span></span>

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a><span data-ttu-id="87f46-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87f46-125">See also</span></span>

* [<span data-ttu-id="87f46-126">SQLite hata kodları</span><span class="sxs-lookup"><span data-stu-id="87f46-126">SQLite Error Codes</span></span>](https://www.sqlite.org/rescode.html)
* [<span data-ttu-id="87f46-127">SQLite Içinde dosya kilitleme</span><span class="sxs-lookup"><span data-stu-id="87f46-127">File Locking In SQLite</span></span>](https://www.sqlite.org/lockingv3.html)
* [<span data-ttu-id="87f46-128">Paylaşılan önbellek modu</span><span class="sxs-lookup"><span data-stu-id="87f46-128">Shared-Cache Mode</span></span>](https://www.sqlite.org/sharedcache.html)
* [<span data-ttu-id="87f46-129">Önceden yazma günlüğü</span><span class="sxs-lookup"><span data-stu-id="87f46-129">Write-Ahead Logging</span></span>](https://www.sqlite.org/wal.html)
