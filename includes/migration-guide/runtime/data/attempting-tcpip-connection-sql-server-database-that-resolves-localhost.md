---
ms.openlocfilehash: a4b8a03661650a3ef1d96b656798c3c3d39a5705
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58467088"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Bir SQL Server veritabanına çözümler TCP/IP bağlantı kurmaya çalışan `localhost` başarısız

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1, çözümler bir SQL Server veritabanına TCP/IP bağlantı kurmaya çalışan <code>localhost</code> hatasıyla başarısız oluyor &quot;bir SQL Server bağlantısı kurulurken ağla ilgili veya örneğe özel bir hata oluştu. Sunucu bulunamadı veya erişilebilir durumda değildi. Örnek adının doğru olduğundan ve SQL Server Uzak bağlantılara izin verecek şekilde yapılandırıldığını doğrulayın. (sağlayıcısı: SQL ağ arabirimleri, hata: 26 - Server/örneği belirtilen bulma hatası)&quot;|
|Öneri|Bu sorun giderilmiştir ve .NET Framework 4.6.2 önceki davranış geri. Çözümler bir SQL Server veritabanına bağlanmak için <code>localhost</code>, .NET Framework 4.6.2 yükseltin.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|

