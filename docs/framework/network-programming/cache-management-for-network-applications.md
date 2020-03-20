---
title: Ağ Uygulamaları için Önbellek Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048881"
---
# <a name="cache-management-for-network-applications"></a>Ağ Uygulamaları için Önbellek Yönetimi
Bu <xref:System.Net.WebClient>konu ve ilgili alt konuları, , , <xref:System.Net.WebRequest> <xref:System.Net.HttpWebRequest>ve <xref:System.Net.FtpWebRequest> sınıflar kullanılarak elde edilen kaynaklar için önbelleğe alma açıklar.  
  
 Önbellek, bir uygulama tarafından istenen kaynakların geçici olarak depolanmasını sağlar. Bir uygulama aynı kaynağı birden çok kez isterse, kaynak sunucudan yeniden talep etme yükünden kaçınarak önbellekten döndürülebilir. Önbelleğe alma, istenen bir kaynağı elde etmek için gereken süreyi azaltarak uygulama performansını artırabilir. Önbelleğe alma, sunucuya yapılan seyahat sayısını azaltarak ağ trafiğini de azaltabilir. Önbelleğe alma performansı artırırken, uygulamaya döndürülen kaynağın eskimiş olması riskini artırır, bu da önbelleğe alma kullanılmamışsa sunucu tarafından gönderilen kaynakla aynı olmadığı anlamına gelir.  
  
 Önbelleğe alma, yetkisiz kullanıcıların veya işlemlerin hassas verileri okumasına izin verebilir. Önbelleğe alınmış kimlik doğrulaması yanıtı ek bir yetkilendirme olmadan önbellekten alınabilir. Önbelleğe alma etkinse, <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> bu istek için önbelleğe alma veya devre dışı etme özelliğini değiştirin. <xref:System.Net.WebRequest.CachePolicy%2A> <xref:System.Net.Cache.RequestCacheLevel.BypassCache>  
  
 Güvenlik kaygıları nedeniyle, önbelleğe alma orta katman senaryoları için **önerilmez.**  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Önbellek İlkesi](cache-policy.md)  
 Önbellek ilkesinin ne olduğunu ve nasıl tanımlanacağını açıklar.  
  
 [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)  
 Hypertext Aktarım Protokolü (http ve https) kaynakları için kullanılabilen her konum tabanlı önbellek ilkesi türünü tanımlar.  
  
 [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)  
 Zaman tabanlı önbellek ilkesini özelleştirmek için kullanılabilecek ölçütleri açıklar.  
  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)  
 Önbellek kullanan önbellek ilkeleri ve isteklerini programlı bir şekilde nasıl oluşturacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>, , <xref:System.Net.HttpWebRequest>ve sınıflar kullanılarak elde edilen kaynaklar için önbellek ilkelerini tanımlamak için kullanılan türleri ve <xref:System.Net.FtpWebRequest> sayısallaştırmaları tanımlar.
