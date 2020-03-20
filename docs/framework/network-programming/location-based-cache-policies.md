---
title: Konum Temelli Önbellek İlkeleri
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
ms.openlocfilehash: e6896452fce89f69b40f1d03332355df72d93211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047673"
---
# <a name="location-based-cache-policies"></a>Konum Temelli Önbellek İlkeleri
Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alan geçerli önbelleğe alınmış girişlerin tazeliğini tanımlar. Önbelleğe alınmış bir kaynak, sunucu tarafından belirtilen yeniden doğrulama gereksinimlerini ihlal etmiyorsa geçerlidir. Konum tabanlı önbellek ilkesi, bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> sınıf oluşturucusu kullanılarak programlı olarak oluşturulur. Konum tabanlı ilke türü, bir <xref:System.Net.Cache.RequestCacheLevel> veya <xref:System.Net.Cache.HttpRequestCacheLevel> numaralandırma değeri kullanılarak oluşturucuya aktarılır. Konum tabanlı önbellek ilkeleri oluşturan kod örnekleri [için bkz.](how-to-set-a-location-based-cache-policy-for-an-application.md) Aşağıdaki bölümlerde, Hypertext Transfer Protocol (http ve https) kaynakları için konum tabanlı önbellek ilkesinin her türü açıklayınız.  
  
## <a name="cache-if-available-policy"></a>KullanılabilirSe Önbellek İlke  
 İstenen geçerli bir kaynak yerel önbellekteyse, önbelleğe alınmış kaynak kullanılır; aksi takdirde, kaynak isteği sunucuya gönderilir. İstenilen kaynak istemci ve sunucu arasındaki herhangi bir önbellekte kullanılabilirse, istek bir ara önbellek tarafından karşılanabilir.  
  
## <a name="cache-only-policy"></a>Önbellek Yalnızca İlke  
 İstenen geçerli bir kaynak yerel önbellekteyse, önbelleğe alınmış kaynak kullanılır. Bu önbellek ilkesi düzeyi belirtildiğinde, öğe yerel önbellekte değilse bir <xref:System.Net.WebException> özel durum atılır.  
  
## <a name="cache-or-next-cache-only-policy"></a>Önbellek Veya Sonraki Önbellek Yalnızca İlke  
 İstenen geçerli bir kaynak yerel önbellekte veya yerel alan ağındaki bir ara önbellekteyse, önbelleğe alınmış kaynak kullanılır. Aksi takdirde, bir <xref:System.Net.WebException> özel durum atılır. HTTP önbelleğe alma protokolünde, bu yalnızca önbelleğe alınmış önbellek denetim yönergesi kullanılarak elde edilir.  
  
## <a name="no-cache-no-store-policy"></a>Önbellek Yok Mağaza İlkesi  
 İstenen bir kaynak hiçbir önbellekten kullanılmaz ve hiçbir önbelleğe yerleştirilmez. İstenen bir kaynak yerel önbellekte bulunursa, kaldırılır. Bu ilke düzeyi, ara önbelleklere kaynağı kaldırmaları gerektiğini gösterir. HTTP önbelleğe alma protokolünde, bu, deposuz önbellek denetim yönergesi kullanılarak elde edilir.  
  
## <a name="refresh-policy"></a>Yenileme İlkesi  
 İstenen bir kaynak, sunucudan elde edilmişse veya yerel önbellek dışında bir önbellekte bulunursa kullanılabilir. İstek bir ara önbellek tarafından karşılanabilmesi için önbelleğin önbelleğe alınmış girişini sunucuyla yeniden onaylaması gerekir. HTTP önbelleğe alma protokolünde, bu maksimum yaş = 0 önbellek denetim yönergesi ve no-cache Pragma üstbilgi kullanılarak elde edilir.  
  
## <a name="reload-policy"></a>Yeniden Yükleme İlkesi  
 İstenen kaynaklar sunucudan alınmalıdır. Yanıt yerel önbelleğe kaydedilebilir. HTTP önbelleğe alma protokolünde, bu no-cache önbellek denetim yönergesi ve no-cache Pragma üstbilgi kullanılarak elde edilir.  
  
## <a name="revalidate-policy"></a>İlkeyi Yeniden Geçersiz Say  
 Önbellekteki kaynağın kopyasını sunucudaki kopyayla karşılaştırır. Sunucudaki kopya daha yeniyse, isteği karşılamak için kullanılır ve önbellekteki kopyanın yerine alır. Önbellekteki kopya sunucu kopyasıyla aynıysa, önbelleğe alınmış kopya kullanılır. HTTP önbelleğe alma protokolünde, bu koşullu bir istek kullanılarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [\<requestCaching> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
