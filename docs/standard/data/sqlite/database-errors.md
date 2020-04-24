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
# <a name="database-errors"></a>Veritabanı hataları

<xref:Microsoft.Data.Sqlite.SqliteException>bir SQLite hatası ile karşılaşıldığında oluşturulur. İleti SQLite tarafından sağlanır. Ve `SqliteErrorCode` `SqliteExtendedErrorCode` özellikleri, hatanın SQLite [sonuç kodunu](https://www.sqlite.org/rescode.html) içerir.

Microsoft. Data. SQLite yerel SQLite kitaplığı ile etkileşime geçtiğinde hatalarla karşılaşılabilir. Aşağıdaki listede, hataların gerçekleşebileceği yaygın senaryolar gösterilmektedir:

* Bir bağlantı açılıyor.
* İşlem başlatılıyor.
* Bir komut yürütülüyor.
* Çağrılıyor <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.

Uygulamanızın bu hataları nasıl işleyeceğini dikkatle düşünün.

## <a name="locking-retries-and-timeouts"></a>Kilitleme, yeniden denemeler ve zaman aşımları

SQLite, tabloları ve veritabanı dosyalarını kilitlemek için gelir. Uygulamanız eşzamanlı veritabanı erişimi sağladığından, büyük olasılıkla meşgul ve kilitli hatalarıyla karşılaşırsınız. [Paylaşılan bir önbellek](connection-strings.md#cache) ve [yazma öncesi günlük](async.md)kullanarak birçok hatayı azaltabilirsiniz.

Microsoft. Data. SQLite, meşgul veya kilitli bir hatayla karşılaştığında otomatik olarak yeniden dener veya komut zaman aşımına ulaşılacaktır.

Komutunu ayarlayarak <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>komut zaman aşımını artırabilirsiniz. Varsayılan zaman aşımı 30 saniyedir. Bir değeri zaman `0` aşımı değildir anlamına gelir.

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

Microsoft. Data. SQLite bazen örtük bir komut nesnesi oluşturması gerekir. Örneğin, BeginTransaction sırasında. Bu komutlara ilişkin zaman aşımını ayarlamak için kullanın <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a>Ayrıca bkz.

* [SQLite hata kodları](https://www.sqlite.org/rescode.html)
* [SQLite Içinde dosya kilitleme](https://www.sqlite.org/lockingv3.html)
* [Paylaşılan önbellek modu](https://www.sqlite.org/sharedcache.html)
* [Önceden yazma günlüğü](https://www.sqlite.org/wal.html)
