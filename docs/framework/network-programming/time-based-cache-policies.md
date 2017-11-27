---
title: "Önbellek zaman tabanlı ilkeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d4cfa67d7fba06140838e04bdbff71102a2a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="time-based-cache-policies"></a>Önbellek zaman tabanlı ilkeleri
Bir zamana dayalı önbellek İlkesi üstbilgileri kaynakla döndürülen kaynak alınan saati ve geçerli saati kullanarak önbelleğe alınmış girişleri yenilik tanımlar. Önbellek zaman tabanlı ilke ayarı, kullanabilir <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zaman tabanlı ilke veya özelleştirilmiş bir zamana dayalı ilkesi oluşturun. Varsayılan zaman tabanlı ilke için Köprü Metni Aktarım Protokolü (HTTP) kullanarak elde kaynaklar kullanırken, tam önbellek davranışını 13 ve RFC 2616 14 bölümlerinde belirtilen davranışları ve önbelleğe alınan yanıta dahil üstbilgileri tarafından belirlenir, adresinde [http://www.ietf.org](http://www.ietf.org/). HTTP kaynaklar için varsayılan zaman tabanlı ilke ayarı gösteren kod örneği için bkz: [nasıl yapılır: bir uygulama Default Time-Based önbellek İlkesi ayarlama](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Önbellek ilkeleri oluşturma ve kullanma gösteren kod örnekleri için bkz: [yapılandırma önbelleği ağ uygulamalarda](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Önbelleğe alınan girişlerinin yenilik belirlemek için ölçütü  
 Bir zamana dayalı önbellek İlkesi özelleştirmek için bir veya daha fazla aşağıdaki ölçütleri önbelleğe alınan girdileri yenilik belirlemek için kullanılabilir belirtebilirsiniz:  
  
-   En uzun geçerlilik süresi  
  
-   En fazla eskime durumu  
  
-   Minimum yenilik  
  
-   Önbellek eşitleme tarihi  
  
> [!NOTE]
>  Varsayılan zamana dayalı önbellek İlkesi'ni kullanarak uygulamanız için bir varsayılan önbellek İlkesi ayarı ile karıştırılmamalıdır. Varsayılan zaman tabanlı ilke isteği veya uygulama düzeyinde kullanılabilen belirli bir ilkedir. Varsayılan önbellek İlkesi uygulamanız için bir istekte hiçbir ilkeyi ayarladığınızda, etkinleşir bir (konum temelli veya zamana dayalı) ilkesidir. Uygulamanız için varsayılan bir önbellek ilkesini ayarlama hakkında daha fazla bilgi için bkz: <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>En uzun geçerlilik süresi  
 En uzun geçerlilik süresi İlkesi ölçüt bir kaynağın önbelleğe alınmış bir kopyasını kullanılabilir süreyi belirtir. Kaynağın önbelleğe alınmış kopyasını belirtilen süre miktarını eski ise, kaynak sunucunuzdaki içeriğe karşı denetleyerek gerekiyor.%0. En uzun geçerlilik süresi sona ermeden sonra kullanılmak üzere kaynak olanak tanır, bu ölçütü değil dikkate alınır maksimum eskime durumu değeri de belirtilmedikçe.  
  
### <a name="maximum-staleness"></a>En fazla eskime durumu  
 En fazla eskime durumu ilkesi ölçüt kaynağın önbelleğe alınmış kopyasını kullanılabilir içerik sona erme sonra geçen süreyi belirtir. Bu kaynaklar süresi dolduktan sonra kullanılacak veren yalnızca önbellek İlkesi ölçüttür.  
  
### <a name="minimum-freshness"></a>Minimum yenilik  
 Minimum yenilik İlkesi ölçüt kaynağın önbelleğe alınmış kopyasını kullanılabilir içerik geçerliliği sona ermeden önce geçen süreyi belirtir. Bu ilke, sona erme tarihinden önce süresi dolacak şekilde bir önbellek girişi neden etkisi vardır; Bu nedenle, en fazla eskime durumu ayarlarını ve minimum yenilik karşılıklı olarak birbirini dışlar.  
  
## <a name="cache-synchronization-date"></a>Önbellek eşitleme tarihi  
 Önbellek eşitleme tarih ilkesi ölçütü, sunucunuzdaki içeriğe karşı denetleyerek bir kaynağın önbelleğe alınmış bir kopyasını zaman gerekiyor.%0 belirler. İçeriği, öğenin önbelleğe oluşturulmasından sonra değiştirilmişse, sunucudan alınan, önbellekte saklanan ve uygulamaya döndürdü. İçerik değişmemişse, zaman damgası güncelleştirilir ve uygulama önbelleğe alınmış içeriği alır.  
  
 Önbellek eşitleme tarihi ne zaman önbelleğe alınmış içeriği gerekiyor.%0 mutlak bir tarih belirtmenize olanak tanır. Yeni bir önbellek girişi önbellek eşitleme tarihinden önce en son yeniden doğrulanır, sunucu ile yeniden doğrulanması oluşmaya devam eder. Önbellek girişi önbellek eşitleme tarihinden sonra yeniden doğrulanır ve ek yenilik veya önbelleğe alınan girdinin geçersiz sunucu yeniden doğrulanması gereksinimleri yoktur, önbellek girişi kullanılır. Önbellek eşitleme tarihi gelecekteki bir tarih olarak ayarlanırsa, giriş önbellek eşitleme tarihini geçerse kadar her istendiğinde yeniden doğrulanır.  
  
 Aşağıdaki konular zamana dayalı önbellek İlkesi ölçütlerini birleştirmenin etkileri hakkında bilgi sağlar:  
  
-   [Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve en fazla eskime durumu](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ uygulamaları için önbellek yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum temelli önbellek ilkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Ağ uygulamalarında önbelleğe alma yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
