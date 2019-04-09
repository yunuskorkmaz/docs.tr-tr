---
title: Önbellek İlkesi
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
ms.openlocfilehash: 33043652e11beb374843d43c9683ff4b7928eb3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112807"
---
# <a name="cache-policy"></a>Önbellek İlkesi
Önbellek İlkesi, istenen kaynak önbelleğe alınmış bir kopyasını kullanarak bir istek memnun olup olmadığını belirlemek için kullanılan kuralları tanımlar. Uygulamalar için yenilik istemci önbellek gereksinimleri belirtin, ancak etkili önbellek ilkesini, istemci önbellek gereksinimleri, sunucunun içerik sona erme gereksinimleri ve sunucunun yeniden doğrulama gereksinimlerini göre belirlenir. En yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak için en koruyucu önbellek İlkesi etkileşimi istemci önbellek İlkesi ve sunucu gereksinimleri her zaman sonuçlanır.  
  
 Konum tabanlı veya saat temelli önbellek ilkeleri. Konum temelli önbellek İlkesi burada istenen kaynak gelen gerçekleştirilebilecek göre önbelleğe alınan girişlerin güncellik tanımlar. Saat temelli önbellek İlkesi, kaynak ve geçerli zamanın üstbilgileri döndürülen kaynak alındı, saat kullanarak önbelleğe alınan girişlerin güncellik tanımlar. Çoğu uygulama, RFC 2616 adresinde belirtilen önbellek İlkesi uygulayan varsayılan saat temelli önbellek ilkesini kullanabilirsiniz [Internet Engineering Task Force (IETF)](https://www.ietf.org/) Web sitesi.  
  
 Aşağıdaki tabloda açıklanan sınıflar, önbellek ilkelerini belirtmek için kullanılır.  
  
|Sınıf adı|Açıklama|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Konum temelli ve saat temelli önbellek ilkeleri kullanılarak kaynaklar için temsil <xref:System.Net.HttpWebRequest> nesneleri.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Konum temelli önbellek ilkeleri temsil eder veya <xref:System.Net.Cache.RequestCacheLevel.Default> kullanarak istenen kaynak için saat temelli önbellek İlkesi <xref:System.Net.WebRequest> nesneleri.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Zamana bağlı oluşturmak için kullanılan değerleri belirten <xref:System.Net.Cache.HttpRequestCachePolicy> nesneleri.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Konum ve zaman tabanlı oluşturmak için kullanılan değerleri belirten <xref:System.Net.Cache.HttpRequestCachePolicy> nesneleri.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Konum tabanlı oluşturmak için kullanılan değerleri belirten veya <xref:System.Net.Cache.RequestCacheLevel.Default> zamana bağlı <xref:System.Net.Cache.RequestCachePolicy> nesneleri.|  
  
 Uygulamanız tarafından yapılan tüm isteklere ait ya da tek tek istekler için bir önbellek ilkesi tanımlayabilirsiniz. Bir uygulama düzeyi önbellek ilkesi hem istek düzeyi önbellek İlkesi belirttiğinizde, istek düzeyi ilkesi kullanılır. Programlama yoluyla veya makine yapılandırma dosyaları ve uygulama kullanarak bir uygulama düzeyi önbellek İlkesi belirtebilirsiniz. Daha fazla bilgi için [ \<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Önbellek ilkesi oluşturmak için bir ilke nesnesi bir örneğini oluşturarak oluşturmalısınız <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> sınıfı. Bir isteği ilke belirtmek için isteğin ayarlamak <xref:System.Net.WebRequest.CachePolicy%2A> ilkesi için özellik. Uygulama düzeyi ilke programlı olarak ayarlama, ayarlama <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> ilkesi için özellik.  
  
 Önbellek ilkeleri oluşturma ve kullanma gösteren kod örnekleri için bkz: [ağ uygulamalarında önbelleğe yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
