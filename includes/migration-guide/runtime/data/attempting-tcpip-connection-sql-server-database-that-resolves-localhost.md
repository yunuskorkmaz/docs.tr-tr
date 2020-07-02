---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621818"
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
