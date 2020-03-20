---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237825"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Başarısız olan bir SQL Server veritabanına `localhost` TCP/IP bağlantısı denemesi

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1'de, hatayla birlikte başarısız olmayı çözen <code>localhost</code> bir SQL Server &quot;veritabanına TCP/IP bağlantısı çalışırken, SQL Server'a bağlantı kurarken ağla ilgili veya örne özgü bir hata oluştu. Sunucu bulunamadı veya erişilebilir değildi. Örnek adının doğru olduğunu ve SQL Server'ın uzak bağlantılara izin verecek şekilde yapılandırıldığından doğrulayın. (sağlayıcı: SQL Ağ Arayüzleri, hata: 26 - Hata Konumlandırma Server/Instance Specified)&quot;|
|Öneri|Bu sorun giderildi ve .NET Framework 4.6.2'de önceki davranış geri yüklendi. .NET Framework 4.6.2'ye yükseltmeyi <code>localhost</code>çözen bir SQL Server databsae'ye bağlanmak için.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
