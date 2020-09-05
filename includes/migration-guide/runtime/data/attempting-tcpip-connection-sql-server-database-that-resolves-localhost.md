---
ms.openlocfilehash: bbeca87b3f498213b91d942cc4f197c9d80457a8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497899"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Başarısız olarak çözümlenen bir SQL Server veritabanına TCP/IP bağlantısı kurmaya çalışılıyor `localhost`

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ve 4.6.1 ' de, hata ile başarısız olarak çözümlenen bir SQL Server veritabanına TCP/IP bağlantısı kurmaya çalışırken <code>localhost</code> , &quot; SQL Server bağlantı kurulurken ağla ilgili veya örneğe özgü bir hata oluştu. Sunucu bulunamadı veya erişilebilir değildi. Örnek adının doğru olduğundan ve SQL Server uzak bağlantılara izin verecek şekilde yapılandırıldığından emin olun. (sağlayıcı: SQL ağ arabirimleri, hata: 26-belirtilen sunucu/örnek bulunurken hata oluştu)&quot;

#### <a name="suggestion"></a>Öneri

Bu sorun giderilmiştir ve önceki davranış .NET Framework 4.6.2 geri yüklendi. ' A çözümlenen SQL Server bir veritabanına bağlanmak için <code>localhost</code> .NET Framework 4.6.2 yükseltin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
