---
title: Ağ uygulamaları için önbellek yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c2b27f3516169ee7b90eaa27fbf22ec02fb638fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cache-management-for-network-applications"></a>Ağ uygulamaları için önbellek yönetimi
Kullanarak elde kaynaklar için önbelleğe alma Bu konu ve alt ilgili konuları açıklanmaktadır <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, ve <xref:System.Net.FtpWebRequest> sınıfları.  
  
 Bir önbellek, bir uygulama tarafından istenen kaynakları geçici olarak depolanmasını sağlar. Bir uygulama birden çok kez aynı kaynak isterse, kaynak sunucudan yeniden isteme yükünden kurtularak önbellekten döndürülebilir. Önbelleğe alma, istenen kaynak almak için gereken süreyi azaltarak uygulama performansını iyileştirebilir. Önbelleğe alma sunucuya sayısını azaltarak ağ trafiğini da azaltabilirsiniz. Önbelleğe alma performansını artırır, ancak kaynak döndürülen riskini artırır önbelleğe alma kullanılıyor olsalar, sunucu tarafından gönderilen kaynak özdeş değil, yani eski bir uygulamadır.  
  
 Önbelleğe alma, yetkisiz kullanıcılara veya işlemlere hassas verileri okumak izin verebilir. Önbelleğe alınmış bir kimliği doğrulanmış yanıt ek bir yetkilendirme olmadan önbellekten alınabilir. Önbelleğe alma etkinse değiştirmek <xref:System.Net.WebRequest.CachePolicy%2A> için <xref:System.Net.Cache.RequestCacheLevel.BypassCache> veya <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> bu istek için önbelleğe almayı devre dışı bırakmak için.  
  
 Önbelleğe alma güvenlik sorunları nedeniyle olan **değil** orta katman senaryolar için önerilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 Açıklayan bir önbellek ilkeleri ve nasıl bir tane tanımlayacaksınız.  
  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Her konum temelli önbellek ilkesi için Köprü Metni Aktarım Protokolü (http ve https) kaynaklar kullanılabilir türünü tanımlar.  
  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Bir zamana dayalı önbellek İlkesi özelleştirmek için kullanılan ölçüt açıklar.  
  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Program aracılığıyla önbellek ilkeleri ve önbelleğe alma kullanan istekleri nasıl oluşturulacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net.Cache>  
 Türleri ve kullanarak elde kaynaklar için önbellek ilkelerini tanımlamak için kullanılan numaralandırmaları tanımlar <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, ve <xref:System.Net.FtpWebRequest> sınıfları.
