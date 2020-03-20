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
ms.openlocfilehash: 0edde8e716d5ce3b1444e994234def5835341475
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047120"
---
# <a name="time-based-cache-policies"></a>Saat Temelli Önbellek İlkeleri
Zaman tabanlı önbellek ilkesi, kaynağın alındığı zamanı, üstbilgi kaynağıyla döndürülen zamanı ve geçerli saati kullanarak önbelleğe alınmış girişlerin tazeliğini tanımlar. Zaman tabanlı önbellek ilkesini ayarlarken, zaman <xref:System.Net.Cache.HttpRequestCacheLevel.Default> tabanlı ilkeyi kullanabilir veya özelleştirilmiş zaman tabanlı bir ilke oluşturabilirsiniz. Hypertext Transfer Protocol (HTTP) kullanılarak elde edilen kaynaklar için varsayılan zaman tabanlı ilke yi kullanırken, tam önbellek davranışı önbelleğe alınan yanıtta yer alan üstbilgiler ve [Internet Engineering Task Force (IETF)](https://www.ietf.org/) web sitesinde bulunan RFC 2616'nın 13 ve 14'üncü bölümlerinde belirtilen davranışlar tarafından belirlenir. HTTP kaynakları için varsayılan zaman tabanlı ilkeyi ayarlayan bir kod örneği [için bkz.](how-to-set-the-default-time-based-cache-policy-for-an-application.md) Önbellek ilkeleri oluşturma yı ve kullanmayı gösteren kod örnekleri [için](configuring-caching-in-network-applications.md)bkz.  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Önbelleğe Alınmış Girişlerin Tazeliğini Belirleme Kriterleri  
 Zaman tabanlı önbellek ilkesini özelleştirmek için, önbelleğe alınmış girişlerin tazeliğini belirlemek için aşağıdaki ölçütlerden birinin veya daha fazlasının kullanılacağını belirtebilirsiniz:  
  
- Maksimum yaş  
  
- Maksimum bayatlık  
  
- Minimum tazelik  
  
- Önbellek eşitleme tarihi  
  
> [!NOTE]
> Varsayılan zaman tabanlı önbellek ilkesini kullanmak, uygulamanız için varsayılan önbellek ilkesi ayarlamakla karıştırılmamalıdır. Varsayılan zaman tabanlı ilke, istek veya uygulama düzeyinde kullanılabilecek belirli bir ilkedir. Uygulamanızın varsayılan önbellek ilkesi, istek üzerinde hiçbir ilke ayarlandığında etkili olan bir ilkedir (konum tabanlı veya zaman tabanlı). Uygulamanız için varsayılan önbellek ilkesini ayarlamayla ilgili ayrıntılar için bkz. <xref:System.Net.WebRequest.DefaultCachePolicy%2A>  
  
### <a name="maximum-age"></a>Maksimum Yaş  
 Maksimum yaş ilkesi ölçütü, kaynağın önbelleğe alınmış bir kopyasının kullanabileceği süreyi belirtir. Kaynağın önbelleğe alınmış kopyası belirtilen süreden daha eskiyse, kaynak sunucudaki içeriğe karşı denetleyerek yeniden doğrulanmalıdır. Maksimum yaş, kaynağın süresi dolduktan sonra kullanılmasına izin verecekse, maksimum bayatlık değeri de belirtilmedikçe bu ölçüt ler yerine getirilmez.  
  
### <a name="maximum-staleness"></a>Maksimum Bayatlık  
 Maksimum bayatlık ilkesi ölçütü, kaynağın önbelleğe alınmış kopyasının kullanılabileceğini içerik sona erme tarihinden sonraki süreyi belirtir. Bu, kaynakların süresi dolduktan sonra kullanılmasına izin veren tek önbellek ilkesi ölçütüdür.  
  
### <a name="minimum-freshness"></a>Minimum Tazelik  
 Minimum tazelik ilkesi ölçütü, kaynağın önbelleğe alınmış kopyasının kullanılabileceğini içerik sona ermeden önceki süreyi belirtir. Bu ilke, bir önbellek girişinin son kullanma tarihinden önce sona ermesine neden olabilir; bu nedenle, minimum tazelik ve maksimum bayatlık ayarları birbirini dışlar.  
  
## <a name="cache-synchronization-date"></a>Önbellek Eşitleme Tarihi  
 Önbellek eşitleme tarihi ilkesi ilkesi, kaynağın önbelleğe alınmış bir kopyasının sunucudaki içeriğe karşı denetleyerek ne zaman yeniden geçersiz kılınacağını belirler. Öğe önbelleğe alındıktan sonra içerik değiştiyse, sunucudan alınır, önbellekte depolanır ve uygulamaya döndürülür. İçerik değişmemişse, zaman damgası güncelleştirilir ve uygulama önbelleğe alınmış içeriği alır.  
  
 Önbellek eşitleme tarihi, önbelleğe alınmış içeriğin yeniden geçersiz kılınması gerektiğinde mutlak bir tarih belirtmenize olanak tanır. Önbellek eşitleme tarihinden önce yeni bir önbellek girişi en son yeniden geçersiz kılındıysa, sunucuyla yeniden doğrulama yine de gerçekleşir. Önbellek girişi önbellek eşitleme tarihinden sonra yeniden geçersiz kılındıysa ve önbelleğe alınan girişi geçersiz sayan ek bir tazelik veya sunucu yeniden doğrulama gereksinimi yoksa, önbellekteki giriş kullanılır. Önbellek eşitleme tarihi ileri bir tarihe ayarlanırsa, önbellek eşitleme tarihi geçene kadar giriş her istendiğinde yeniden geçersiz kılınır.  
  
 Aşağıdaki konular, zamana dayalı önbellek ilkesi ölçütlerini birleştirmenin etkileri hakkında bilgi sağlar:  
  
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [\<requestCaching> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
