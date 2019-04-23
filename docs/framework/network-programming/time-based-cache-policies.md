---
title: Saat Temelli Önbellek İlkeleri
ms.date: 03/30/2017
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
ms.openlocfilehash: 0fb9b50fdbc0a1e11992baac684c5e2e8c081f5f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129317"
---
# <a name="time-based-cache-policies"></a>Saat Temelli Önbellek İlkeleri
Bir saat temelli önbellek İlkesi üstbilgileri kaynakla döndürülen kaynak alınmadı zaman ve geçerli zamanı kullanarak önbelleğe alınan girişlerin güncellik tanımlar. Saat temelli önbellek İlkesi ayarlanarak, kullanabilir <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zaman tabanlı bir ilke veya özelleştirilmiş zamana bağlı ilkesi oluşturun. Köprü Metni Aktarım Protokolü (HTTP) kullanılarak elde edilen kaynaklar için varsayılan saat temelli ilkesini kullanarak, tam önbellek davranışını 13 ve RFC 2616 14 bölümlerinde belirtilen davranışları ve önbelleğe alınan yanıta dahil üstbilgileri tarafından belirlenir, kullanılabilir [Internet Engineering Task Force (IETF)](https://www.ietf.org/) Web sitesi. HTTP kaynaklar için varsayılan zaman tabanlı ilke ayarı gösteren bir kod örneği için bkz: [nasıl yapılır: Uygulama için varsayılan saat temelli önbellek İlkesi ayarlama](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Önbellek ilkeleri oluşturma ve kullanma gösteren kod örnekleri için bkz: [ağ uygulamalarında önbelleğe yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Önbelleğe alınan girişlerin Güncellik belirlemek için ölçütleri  
 Bir saat temelli önbellek İlkesi özelleştirmek için önbelleğe alınan girişlerin güncellik belirlemek için bir veya daha fazla aşağıdaki ölçütleri kullanılabilir belirtebilirsiniz:  
  
-   En uzun geçerlilik süresi  
  
-   En fazla eskime  
  
-   En az eskime  
  
-   Önbellek eşitleme tarihi  
  
> [!NOTE]
>  Varsayılan saat temelli önbellek ilkesini kullanarak uygulamanız için varsayılan bir önbellek İlkesi ayarlama ile karıştırılmamalıdır. Zamana bağlı varsayılan ilke isteği veya uygulama düzeyinde kullanılabilen belirli bir ilkedir. Varsayılan önbellek ilkesini uygulamanız için bir istek üzerinde ayarlanan ilke olduğunda etkinleşir bir (konum tabanlı veya zamana bağlı) ilkedir. Uygulamanız için varsayılan bir önbellek İlkesi ayarlama hakkında daha fazla bilgi için bkz <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>En uzun geçerlilik süresi  
 En yüksek yaşı İlkesi ölçütü bir kaynağı önbelleğe alınmış bir kopyasını kullanılabilir süreyi belirtir. Kaynağın önbelleğe alınmış kopyasını belirtilen süre miktarını eski ise, kaynak sunucunuzdaki içeriğe karşı denetleyerek gerekiyor.%0. En uzun geçerlilik süresi, süresi dolduktan sonra kullanılacak kaynak izin verir, bu ölçütü değil dikkate alınır en fazla eskime değeri de belirtilmedikçe.  
  
### <a name="maximum-staleness"></a>En fazla eskime  
 En fazla eskime ilke ölçütü kaynak kopyasının kullanılabilir içerik sona erme sonra sürenin uzunluğunu belirtir. Bu kaynakları süresi dolduktan sonra kullanılacak veren tek önbellek İlkesi ölçüttür.  
  
### <a name="minimum-freshness"></a>En az eskime  
 En az eskime ilke ölçütü kaynak kopyasının kullanılabilir içerik süresi dolmadan önce sürenin uzunluğunu belirtir. Bu ilke, sona erme tarihinden önce süresi dolacak şekilde bir önbellek girdisi neden etkisi vardır; Bu nedenle, en fazla eskime ayarları ve en az eskime birbirini dışlar.  
  
## <a name="cache-synchronization-date"></a>Önbellek eşitleme tarihi  
 Önbellek eşitleme tarihi ilke ölçütü ne zaman önbelleğe alınmış bir kopyasını bir kaynak sunucunuzdaki içeriğe karşı denetleyerek gerekiyor.%0 belirler. İçeriği, öğenin önbelleğe alınmış bu yana değişti, sunucudan alınan, önbellekte saklanan ve uygulamaya döndürülen. İçerik değişmemişse, zaman damgası güncelleştirilir ve uygulama, önbelleğe alınmış içeriği alır.  
  
 Önbellek eşitleme tarihi ne zaman önbelleğe alınan içerikler gerekiyor.%0 mutlak bir tarih belirtmenizi sağlar. Yeni bir önbellek girdisi önbellek eşitleme tarihten önce en son yeniden doğrulanır, yeniden doğrulanırken sunucu yine de gerçekleşir. Önbellek girişi önbellek eşitleme tarihinden sonra yeniden doğrulanır ve ek güncellik veya önbelleğe alınmış giriş geçersiz sunucu yeniden doğrulama gereksinimleri yoktur, önbellek girişi kullanılır. Önbellek eşitleme tarihi bir tarihe ayarlarsanız, giriş önbellek eşitleme tarihi geçinceye kadar istek her zaman yeniden doğrulanır.  
  
 Aşağıdaki konular, saat temelli önbellek İlkesi ölçütlerini birleştirme etkileri hakkında bilgi sağlar:  
  
-   [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
