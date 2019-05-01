---
title: Ağ Uygulamaları için Önbellek Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 265b4e451ebb76dbabe0d3e0df065504a3891f32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033169"
---
# <a name="cache-management-for-network-applications"></a>Ağ Uygulamaları için Önbellek Yönetimi
Bu konu ve alt ilgili konuları kullanılarak elde edilen kaynaklar için önbelleğe alma açıklayan <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, ve <xref:System.Net.FtpWebRequest> sınıfları.  
  
 Geçici depolama bir uygulama tarafından istenen kaynak, bir önbellek sağlar. Bir uygulama birden çok kez aynı kaynak isterse, kaynak sunucudan yeniden isteme yükünden önbellekten döndürülebilir. Önbelleğe alma işlemi, istenen kaynak almak için gereken süreyi azaltarak uygulama performansı artırabilir. Önbelleğe alma sunucuya sayısını azaltarak ağ trafiğini de azaltabilir. Önbelleğe alma performansını artırır, ancak kaynak döndürülen riskini artırır. eski önbelleğe alma kullanımda değilse, sunucu tarafından gönderilen kaynak aynı değil, yani bir uygulamadır.  
  
 Önbelleğe alma, yetkisiz kullanıcılara veya işlemlere hassas verileri okumak izin verebilir. Önbelleğe alınmış bir kimliği doğrulanmış yanıt, ek bir yetkilendirme olmadan önbellekten alınabilir. Önbelleğe alma etkinse değiştirmek <xref:System.Net.WebRequest.CachePolicy%2A> için <xref:System.Net.Cache.RequestCacheLevel.BypassCache> veya <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> bu istek için önbelleğe alma devre dışı bırakmak için.  
  
 Önbelleğe alma, güvenlik kaygıları nedeniyle olduğunu **değil** orta katman senaryoları için önerilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 Açıklayan bir önbellek İlkesi ve nasıl bir tane tanımlayacaksınız.  
  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Konum temelli önbellek ilkesi için Köprü Metni Aktarım Protokolü (http ve https) kaynaklar kullanılabilir her türünü tanımlar.  
  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Bir saat temelli önbellek İlkesi özelleştirmek için kullanılan ölçütleri açıklanmaktadır.  
  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Önbellek ilkeleri ve önbelleğe almayı kullanmak istekleri program aracılığıyla oluşturmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net.Cache>  
 Kullanılarak elde edilen kaynaklarının önbellek ilkelerini tanımlamak için kullanılan sabit listeleri ve türlerini tanımlayan <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, ve <xref:System.Net.FtpWebRequest> sınıfları.
