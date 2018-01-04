---
title: "Ağ uygulamaları için önbellek yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 458a1e67e9ca4ff3a36f1b0c69fcc4bdc00be3e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
