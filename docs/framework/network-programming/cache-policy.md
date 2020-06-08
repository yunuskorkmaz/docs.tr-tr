---
title: Önbellek İlkesi
description: Bir isteğin, istenen kaynağın önbelleğe alınmış bir kopyası kullanılarak karşılanıp karşılanamayacağını belirten kurallar hakkında bilgi edinin.
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
ms.openlocfilehash: d63d2b6bf8426968d2120647c8ecea2b7602825a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502671"
---
# <a name="cache-policy"></a>Önbellek İlkesi
Önbellek ilkesi, istenen kaynağın önbelleğe alınmış bir kopyasını kullanarak bir isteğin karşılanıp karşılanamayacağını belirlemede kullanılan kuralları tanımlar. Uygulamalar, yenilik için istemci önbelleği gereksinimlerini belirtir, ancak etkili önbellek ilkesi istemci önbellek gereksinimleriyle, sunucunun içerik süre sonu gereksinimlerine ve sunucunun yeniden doğrulama gereksinimlerine göre belirlenir. İstemci önbellek ilkesinin ve sunucu gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesiyle sonuçlanır, bu da en son içerik istemci uygulamasına geri döndürüldüğünden emin olur.  
  
 Önbellek ilkeleri konum tabanlı ya da zaman tabanlıdır. Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alarak önbelleğe alınmış girişlerin yeniliği tanımlar. Zaman tabanlı önbellek ilkesi, kaynağın alındığı zamanı, kaynakla döndürülen üstbilgileri ve geçerli saati kullanarak önbelleğe alınmış girişlerin yeniliği tanımlar. Çoğu uygulama, [Internet Mühendisliği görev gücü (IETF)](https://www.ietf.org/) Web sitesinde KULLANILABILIR olan RFC 2616 ' de belirtilen önbelleğe alma ilkesini uygulayan varsayılan zaman tabanlı önbellek ilkesini kullanabilir.  
  
 Aşağıdaki tabloda açıklanan sınıflar önbellek ilkelerini belirtmek için kullanılır.  
  
|Sınıf adı|Description|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Nesneler kullanılarak istenen kaynaklar için konum tabanlı ve zaman tabanlı önbellek ilkelerini temsil eder <xref:System.Net.HttpWebRequest> .|  
|<xref:System.Net.Cache.RequestCachePolicy>|<xref:System.Net.Cache.RequestCacheLevel.Default>Nesneler kullanılarak istenen kaynaklar için konum tabanlı önbellek ilkelerini veya zaman tabanlı önbellek ilkesini temsil eder <xref:System.Net.WebRequest> .|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Zamana dayalı nesneler oluşturmak için kullanılan değerleri belirtir <xref:System.Net.Cache.HttpRequestCachePolicy> .|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Konum tabanlı ve zaman tabanlı nesneler oluşturmak için kullanılan değerleri belirtir <xref:System.Net.Cache.HttpRequestCachePolicy> .|  
|<xref:System.Net.Cache.RequestCacheLevel>|Konum tabanlı veya zaman tabanlı nesneler oluşturmak için kullanılan değerleri belirtir <xref:System.Net.Cache.RequestCacheLevel.Default> <xref:System.Net.Cache.RequestCachePolicy> .|  
  
 Uygulamanız veya tek istekler tarafından yapılan tüm istekler için önbellek ilkesi tanımlayabilirsiniz. Hem uygulama düzeyi önbellek ilkesi hem de istek düzeyi önbellek ilkesi belirttiğinizde, istek düzeyi ilke kullanılır. Program aracılığıyla veya uygulama ya da makine yapılandırma dosyalarını kullanarak uygulama düzeyi önbellek ilkesi belirtebilirsiniz. Daha fazla bilgi için bkz. [ \<requestCaching> öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Önbellek ilkesi oluşturmak için veya sınıfının bir örneğini oluşturarak bir ilke nesnesi oluşturmanız gerekir <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> . İlkeyi bir istek üzerinde belirtmek için, isteğin <xref:System.Net.WebRequest.CachePolicy%2A> özelliğini ilke nesnesine ayarlayın. Uygulama düzeyindeki bir ilkeyi programlı olarak ayarlarken, <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> özelliği ilke nesnesine ayarlayın.  
  
 Önbellek ilkeleri oluşturmayı ve kullanmayı gösteren kod örnekleri için bkz. [Ağ uygulamalarında önbelleğe alma yapılandırma](configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
