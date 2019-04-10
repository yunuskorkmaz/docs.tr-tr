---
ms.openlocfilehash: 88d6c166acf9e9ab72c2713b575a8453779f70d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234325"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Bir SQL Server veritabanına çözümler TCP/IP bağlantı kurmaya çalışan `localhost` başarısız

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1, çözümler bir SQL Server veritabanına TCP/IP bağlantı kurmaya çalışan <code>localhost</code> hatasıyla başarısız oluyor &quot;bir SQL Server bağlantısı kurulurken ağla ilgili veya örneğe özel bir hata oluştu. Sunucu bulunamadı veya erişilebilir durumda değildi. Örnek adının doğru olduğundan ve SQL Server Uzak bağlantılara izin verecek şekilde yapılandırıldığını doğrulayın. (sağlayıcısı: SQL ağ arabirimleri, hata: 26 - Server/örneği belirtilen bulma hatası)&quot;|
|Öneri|Bu sorun giderilmiştir ve .NET Framework 4.6.2 önceki davranış geri. Çözümler bir SQL Server veritabanına bağlanmak için <code>localhost</code>, .NET Framework 4.6.2 yükseltin.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
