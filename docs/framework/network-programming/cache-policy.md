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
ms.openlocfilehash: 2d3d85ebd80f417ebd0fa0e619097e15f2a6a39b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048771"
---
# <a name="cache-policy"></a>Önbellek İlkesi
Önbellek ilkesi, istenen kaynağın önbelleğe alınmış bir kopyasını kullanarak bir isteğin karşılanıp karşılanamayacağını belirlemek için kullanılan kuralları tanımlar. Uygulamalar tazelik için istemci önbellek gereksinimlerini belirtir, ancak etkili önbellek ilkesi istemci önbellek gereksinimleri, sunucunun içerik son kullanma gereksinimleri ve sunucunun yeniden doğrulama gereksinimleri tarafından belirlenir. İstemci önbellek ilkesi ve sunucu gereksinimleri etkileşimi, en yeni içeriğin istemci uygulamasına döndürülmesini sağlamaya yardımcı olmak için her zaman en tutucu önbellek ilkesiyle sonuçlanır.  
  
 Önbellek ilkeleri konum tabanlı veya zaman tabanlıdır. Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alan önbelleğe alınmış girişlerin tazeliğini tanımlar. Zaman tabanlı önbellek ilkesi, kaynağın alındığı zamanı, üstbilgi kaynağıyla döndürülen zamanı ve geçerli saati kullanarak önbelleğe alınmış girişlerin tazeliğini tanımlar. Çoğu uygulama, [Internet Engineering Task Force (IETF)](https://www.ietf.org/) web sitesinde bulunan RFC 2616'da belirtilen önbelleğe alma ilkesini uygulayan varsayılan zaman tabanlı önbellek ilkesini kullanabilir.  
  
 Aşağıdaki tabloda açıklanan sınıflar önbellek ilkelerini belirtmek için kullanılır.  
  
|Sınıf adı|Açıklama|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Nesneler kullanılarak <xref:System.Net.HttpWebRequest> istenen kaynaklar için konum tabanlı ve zamana dayalı önbellek ilkelerini temsil eder.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Nesneleri kullanarak <xref:System.Net.WebRequest> istenen kaynaklar için <xref:System.Net.Cache.RequestCacheLevel.Default> konum tabanlı önbellek ilkelerini veya zaman tabanlı önbellek ilkesini temsil eder.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Zaman tabanlı <xref:System.Net.Cache.HttpRequestCachePolicy> nesneler oluşturmak için kullanılan değerleri belirtir.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Konum tabanlı ve zaman tabanlı <xref:System.Net.Cache.HttpRequestCachePolicy> nesneler oluşturmak için kullanılan değerleri belirtir.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Konum tabanlı veya <xref:System.Net.Cache.RequestCacheLevel.Default> zaman tabanlı <xref:System.Net.Cache.RequestCachePolicy> nesneler oluşturmak için kullanılan değerleri belirtir.|  
  
 Uygulamanız veya bireysel istekler için yapılan tüm istekler için bir önbellek ilkesi tanımlayabilirsiniz. Hem uygulama düzeyinde önbellek ilkesi ni hem de istek düzeyi önbellek ilkesini belirttiğiniz zaman, istek düzeyi ilkesi kullanılır. Uygulama düzeyinde önbellek ilkesini programlı olarak veya uygulama veya makine yapılandırma dosyalarını kullanarak belirtebilirsiniz. Daha fazla bilgi için isteğe> [ \<Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)bakın.  
  
 Önbellek ilkesi oluşturmak için, bir ilke nesnesi <xref:System.Net.Cache.RequestCachePolicy> oluşturarak bir ilke nesnesi veya <xref:System.Net.Cache.HttpRequestCachePolicy> sınıf bir örnek oluşturmanız gerekir. İstek teki ilkeyi belirtmek için, <xref:System.Net.WebRequest.CachePolicy%2A> isteğin özelliğini ilke nesnesine ayarlayın. Uygulama düzeyi ilkesini programlı bir şekilde <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> ayarlarken, özelliği ilke nesnesine ayarlayın.  
  
 Önbellek ilkeleri oluşturma yı ve kullanmayı gösteren kod örnekleri [için](configuring-caching-in-network-applications.md)bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
