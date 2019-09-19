---
title: Ağ Uygulamaları için Önbellek Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048881"
---
# <a name="cache-management-for-network-applications"></a>Ağ Uygulamaları için Önbellek Yönetimi
Bu konu ve ilgili <xref:System.Net.WebClient>alt konuları <xref:System.Net.HttpWebRequest>, <xref:System.Net.WebRequest>,, ve <xref:System.Net.FtpWebRequest> sınıfları kullanılarak elde edilen kaynaklar için önbelleğe almayı anlatmaktadır.  
  
 Önbellek, bir uygulama tarafından istenen kaynakların geçici olarak depolanmasını sağlar. Bir uygulama aynı kaynağı birden çok kez isterse, kaynak önbellekten döndürülebileceğinden, sunucudan yeniden istek yükünü ortadan kaldırır. Önbelleğe alma, istenen bir kaynağı almak için gereken süreyi azaltarak uygulama performansını iyileştirebilir. Önbelleğe alma, sunucuya gidiş dönüş sayısını azaltarak da ağ trafiğini azaltabilir. Önbelleğe alma performansı artırırken, uygulamaya döndürülen kaynağın eskimiş olması, yani önbelleğe alma kullanımda değilse sunucu tarafından gönderilen kaynakla aynı olmaması anlamına gelir.  
  
 Önbelleğe alma, yetkisiz kullanıcıların veya işlemlerin hassas verileri okumasına izin verebilir. Önbelleğe alınan kimliği doğrulanmış bir yanıt, ek bir yetkilendirme olmadan önbellekten alınabilir. Önbelleğe alma etkinse, bu istek için <xref:System.Net.WebRequest.CachePolicy%2A> önbelleğe <xref:System.Net.Cache.RequestCacheLevel.BypassCache> almayı <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> devre dışı bırakmak için veya olarak değiştirin.  
  
 Güvenlik sorunları nedeniyle, orta katman senaryolarında önbelleğe **alma önerilmez.**  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Önbellek İlkesi](cache-policy.md)  
 Önbellek ilkesinin ne olduğunu ve bir tane tanımlanacağını açıklar.  
  
 [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)  
 Köprü Metni Aktarım Protokolü (http ve https) kaynakları için kullanılabilen her bir konum tabanlı önbellek ilkesi türünü tanımlar.  
  
 [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)  
 Zaman tabanlı önbellek ilkesini özelleştirmek için kullanılabilecek kriterleri açıklar.  
  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)  
 Program aracılığıyla önbellek ilkelerinin ve önbelleğe alma kullanan isteklerin nasıl oluşturulduğunu açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest> ,<xref:System.Net.HttpWebRequest>Ve sınıfları<xref:System.Net.FtpWebRequest> kullanılarak elde edilen kaynaklar için önbellek ilkelerini tanımlamak üzere kullanılan türleri ve numaralandırmaları tanımlar.
