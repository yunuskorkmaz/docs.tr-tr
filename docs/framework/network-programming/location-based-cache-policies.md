---
title: Konum temelli önbellek ilkeleri
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b4109cef8d527d397903854e05a2204a3e551938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394520"
---
# <a name="location-based-cache-policies"></a>Konum temelli önbellek ilkeleri
Konum temelli önbellek İlkesi, istenen kaynak gelen gerçekleştirilebilecek göre geçerli önbelleğe alınan girdileri yenilik tanımlar. Önbelleğe alınan bir kaynağın geçerli olduğu kullanmadan yoksa sunucu belirtilen COLLECTION gereksinimleri ihlal değil. Konum temelli önbellek İlkesi kullanılarak programlı olarak oluşturulan bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> sınıfı oluşturucusu. Konum tabanlı ilke türünü Oluşturucusu kullanmaya geçirilen bir <xref:System.Net.Cache.RequestCacheLevel> veya <xref:System.Net.Cache.HttpRequestCacheLevel> numaralandırma değeri. Konum temelli önbellek ilkeleri oluşturma kod örnekleri için bkz [nasıl yapılır: bir uygulama için bir konum temelli önbellek İlkesi ayarlamak](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). Aşağıdaki bölümlerde her Köprü Metni Aktarım Protokolü (http ve https) kaynaklar için önbellek konumu tabanlı ilke türü açıklanmaktadır.  
  
## <a name="cache-if-available-policy"></a>Varsa önbellek İlkesi  
 Geçerli bir istenen kaynak yerel önbellekte yer alıyorsa, önbelleğe alınan kaynak kullanılır; Aksi halde, kaynak isteği sunucuya gönderilir. İstenen kaynak, istemci ve sunucu arasındaki tüm önbelleğindeki kullanılabilir durumda, istek bir ara önbelleğinin karşılanabilir.  
  
## <a name="cache-only-policy"></a>Önbellek yalnızca İlkesi  
 Geçerli bir istenen kaynak yerel önbellekte yer alıyorsa, önbelleğe alınan kaynak kullanılır. Bu önbellek ilkesi düzeyi belirtildiğinde, bir <xref:System.Net.WebException> öğesi yerel önbellekte değilse, özel durum.  
  
## <a name="cache-or-next-cache-only-policy"></a>Önbellek veya sonraki yalnızca ilke önbelleğe alma  
 Geçerli bir istenen kaynak yerel önbelleği veya bir ara önbelleği yerel ağda ise, önbelleğe alınan kaynak kullanılır. Aksi halde, bir <xref:System.Net.WebException> özel durumu oluşur. HTTP protokolü önbelleğe alma, bu yalnızca-IF-önbellek önbelleğe alınmış denetim yönergesi kullanılarak gerçekleştirilir.  
  
## <a name="no-cache-no-store-policy"></a>Hayır önbellek Hayır depolamak İlkesi  
 İstenen kaynak herhangi önbellekten asla kullanılmaz ve hiçbir zaman bir önbellekte yerleştirilir. İstenen kaynak yerel önbellekte varsa kaldırılır. Bu ilke düzeyi, bunlar da kaynak kaldırmalısınız Ara önbellekleri gösterir. HTTP protokolü önbelleğe alma, bu Hayır deposu önbellek denetimi yönergesi kullanılarak gerçekleştirilir.  
  
## <a name="refresh-policy"></a>İlke yenileme  
 İstenen kaynak sunucudan alınan veya bir önbellek yerel önbelleği dışında bulunan kullanılabilir. İstek bir ara önbelleği tarafından karşılanması önce o önbellek sunucusu ile önbelleğe alınmış girdisini düzeltin gerekir. HTTP protokolü önbelleğe alma, bu, max-age kullanılarak gerçekleştirilir = 0 önbellek denetimi yönergesi ve no cache Pragma üstbilgisi.  
  
## <a name="reload-policy"></a>İlkeyi yeniden yüklemek  
 İstenen kaynak sunucudan alınması gerekir. Yanıt yerel önbelleğe kaydedilmiş olabilir. HTTP protokolü önbelleğe alma, bu no-cache önbelleği denetim yönergesi ve no cache Pragma üstbilgisi kullanılarak gerçekleştirilir.  
  
## <a name="revalidate-policy"></a>İlke düzeltin  
 Kaynak önbelleğinde kopyasını sunucudaki kopyayla karşılaştırır. Sunucudaki kopyası yeniyse isteği karşılamak için kullanılır ve önbelleğinde kopyasının yerini alır. Önbelleğe alınan kopya önbelleğinde kopyalama sunucu kopyası ile aynı olduğunda kullanılır. HTTP protokolü önbelleğe alma, bu koşullu istek kullanarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
