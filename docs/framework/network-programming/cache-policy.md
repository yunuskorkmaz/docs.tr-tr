---
title: "Önbellek İlkesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 375c3b44f505a9bf36ce721c5ccde9b888114309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy"></a>Önbellek İlkesi
Önbellek İlkesi, istenen kaynak önbelleğe alınmış bir kopyasını kullanarak bir istek yerine olup olmadığını belirlemek için kullanılan kuralları tanımlar. İstemci önbellek gereksinimleri yenilik uygulamaları belirtin, ancak etkili önbellek ilkesini istemci önbellek gereksinimleri, sunucunun içerik sona erme gereksinimleri ve sunucunun yeniden doğrulanması gereksinimleri tarafından belirlenir. İstemci önbellek İlkesi ve sunucu gereksinimleri etkileşimini her zaman en yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak üzere en koruyucu önbellek İlkesi sonuçlanır.  
  
 Önbellek konumu tabanlı ya da zaman tabanlı ilkelerdir. Konum temelli önbellek İlkesi, istenen kaynak gelen gerçekleştirilebilecek göre önbelleğe alınan girdileri yenilik tanımlar. Bir zamana dayalı önbellek İlkesi üstbilgileri kaynak ve geçerli saati ile döndürülen kaynak alındı, saat kullanarak önbelleğe alınmış girişleri yenilik tanımlar. Çoğu uygulama RFC 2616, adresinde belirtilen önbellek İlkesi uygulayan varsayılan zamana dayalı önbellek ilkesini kullanabilirsiniz [http://www.ietf.org](http://www.ietf.org/).  
  
 Aşağıdaki tabloda açıklanan sınıfları önbellek ilkeleri belirtmek için kullanılır.  
  
|Sınıf adı|Açıklama|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Kullanarak istenen kaynaklar için önbellek konumu ve zaman tabanlı ilkeleri temsil eden <xref:System.Net.HttpWebRequest> nesneleri.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Konum temelli önbellek ilkeleri temsil eder veya <xref:System.Net.Cache.RequestCacheLevel.Default> kullanarak istenen kaynaklar için zamana dayalı önbellek İlkesi <xref:System.Net.WebRequest> nesneleri.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Zamana bağlı oluşturmak için kullanılan değerleri belirten <xref:System.Net.Cache.HttpRequestCachePolicy> nesneleri.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Konum ve zaman tabanlı oluşturmak için kullanılan değerleri belirten <xref:System.Net.Cache.HttpRequestCachePolicy> nesneleri.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Konum temelli oluşturmak için kullanılan değerleri belirtir veya <xref:System.Net.Cache.RequestCacheLevel.Default> zamana dayalı <xref:System.Net.Cache.RequestCachePolicy> nesneleri.|  
  
 İstekleri ayrı ayrı veya uygulamanız tarafından yapılan tüm istekleri için bir önbellek ilkesi tanımlayabilirsiniz. Uygulama düzeyi önbellek İlkesi ve bir istek düzeyi önbellek İlkesi belirttiğinizde, istek düzeyi ilkesi kullanılır. Program aracılığıyla veya uygulama veya makine yapılandırma dosyalarını kullanarak bir uygulama düzeyi önbellek İlkesi belirtebilirsiniz. Daha fazla bilgi için bkz: [ \<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Önbellek ilkesi oluşturmak için bir ilke nesnesinin bir örneğini oluşturarak oluşturmalısınız <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> sınıfı. Bir isteği ilkesi belirtmek için isteğin ayarlamak <xref:System.Net.WebRequest.CachePolicy%2A> İlkesi nesnesine özelliği. Bir uygulama düzeyi ilkesi programlı olarak ayarlanırken ayarlamak <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> İlkesi nesnesine özelliği.  
  
 Önbellek ilkeleri oluşturma ve kullanma gösteren kod örnekleri için bkz: [yapılandırma önbelleği ağ uygulamalarda](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ uygulamaları için önbellek yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Konum temelli önbellek ilkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Önbellek zaman tabanlı ilkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Ağ uygulamalarında önbelleğe alma yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
