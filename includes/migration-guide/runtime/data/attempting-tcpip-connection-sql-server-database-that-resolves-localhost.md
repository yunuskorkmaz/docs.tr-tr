---
ms.openlocfilehash: 8ac6d50b192001f6d924b2ffe4a367a33fc2c689
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857578"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Bir SQL Server veritabanına çözümler TCP/IP bağlantı kurmaya çalışan `localhost` başarısız

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1, çözümler bir SQL Server veritabanına TCP/IP bağlantı kurmaya çalışan <code>localhost</code> hatasıyla başarısız oluyor &quot;bir SQL Server bağlantısı kurulurken ağla ilgili veya örneğe özel bir hata oluştu. Sunucu bulunamadı veya erişilebilir durumda değildi. Örnek adının doğru olduğundan ve SQL Server Uzak bağlantılara izin verecek şekilde yapılandırıldığını doğrulayın. (sağlayıcısı: SQL ağ arabirimleri, hata: 26 - Server/örneği belirtilen bulma hatası)&quot;|
|Öneri|Bu sorun giderilmiştir ve .NET Framework 4.6.2 önceki davranış geri. Bağlanmak için çözümler bir SQL Server ı <code>localhost</code>, .NET Framework 4.6.2 yükseltin.|
|`Scope`|Küçük|
|Version|4.6|
|Type|Çalışma zamanı|

