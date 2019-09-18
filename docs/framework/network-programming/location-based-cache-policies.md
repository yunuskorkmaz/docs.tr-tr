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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047673"
---
# <a name="location-based-cache-policies"></a>Konum Temelli Önbellek İlkeleri
Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alarak geçerli önbelleğe alınmış girişlerin yeniliği tanımlar. Önbelleğe alınmış bir kaynak, kullanılması durumunda sunucu tarafından belirtilen yeniden doğrulama gereksinimlerini ihlal etmezse geçerli olur. Konum tabanlı önbellek ilkesi, veya <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> sınıf oluşturucusu kullanılarak programlı bir şekilde oluşturulur. Konum tabanlı ilke türü, bir <xref:System.Net.Cache.RequestCacheLevel> veya <xref:System.Net.Cache.HttpRequestCacheLevel> numaralandırma değeri kullanılarak oluşturucuya geçirilir. Konum tabanlı önbellek ilkeleri oluşturan kod örnekleri için bkz [. nasıl yapılır: Bir uygulama](how-to-set-a-location-based-cache-policy-for-an-application.md)Için konum tabanlı önbellek ilkesi ayarlayın. Aşağıdaki bölümlerde, Köprü Metni Aktarım Protokolü (http ve https) kaynakları için her konum tabanlı önbellek ilkesi türü açıklanmaktadır.  
  
## <a name="cache-if-available-policy"></a>Kullanılabilir Ilke varsa önbelleğe al  
 Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır; Aksi takdirde, kaynak isteği sunucuya gönderilir. İstenen kaynak, istemci ve sunucu arasındaki herhangi bir önbellekte kullanılabiliyorsa, istek bir ara önbellek tarafından karşılanabilir.  
  
## <a name="cache-only-policy"></a>Yalnızca önbellek Ilkesi  
 Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır. Bu önbellek ilkesi düzeyi belirtildiğinde, öğe yerel önbellekte <xref:System.Net.WebException> değilse bir özel durum oluşturulur.  
  
## <a name="cache-or-next-cache-only-policy"></a>Yalnızca önbellek veya sonraki önbellek Ilkesi  
 Geçerli bir istenen kaynak yerel önbellekte veya yerel alan ağı üzerindeki ara önbellekte ise, önbelleğe alınmış kaynak kullanılır. Aksi takdirde, <xref:System.Net.WebException> bir özel durum oluşturulur. HTTP önbelleğe alma protokolünde, bu, tek-if-önbelleğe alınmış önbellek denetim yönergesi kullanılarak elde edilir.  
  
## <a name="no-cache-no-store-policy"></a>Önbellekte depolama Ilkesi yok  
 İstenen bir kaynak herhangi bir önbellekten hiçbir şekilde kullanılmaz ve hiçbir şekilde hiçbir önbelleğe yerleştirilmez. İstenen bir kaynak yerel önbellekte mevcutsa, kaldırılır. Bu ilke düzeyi ara önbelleklerin kaynağı kaldırması gerektiğini gösterir. HTTP önbelleğe alma protokolünde, bu, depolama önbelleği denetim yönergesi kullanılarak elde edilir.  
  
## <a name="refresh-policy"></a>Ilkeyi Yenile  
 İstenen kaynak, sunucudan elde edilmişse veya yerel önbellek dışında bir önbellekte bulunursa kullanılabilir. İstek bir ara önbellek tarafından karşılanmadan önce, bu önbelleğin sunucu ile önbelleğe alınmış girişini yeniden doğrulaması gerekir. HTTP önbelleğe alma protokolünde, bu, maksimum yaş = 0 önbellek denetim yönergesi ve No-Cache pragma üst bilgisi kullanılarak elde edilir.  
  
## <a name="reload-policy"></a>Ilkeyi yeniden yükle  
 İstenen kaynaklar sunucudan alınmalıdır. Yanıt, yerel önbellekte kaydedilmiş olabilir. HTTP önbelleğe alma protokolünde, bu, önbellek önbelleği denetim yönergesi ve No-Cache pragma üst bilgisi kullanılarak elde edilir.  
  
## <a name="revalidate-policy"></a>Ilkeyi yeniden doğrula  
 Önbellekteki kaynağın kopyasını sunucudaki kopyayla karşılaştırır. Sunucu üzerindeki kopya yeniyse, isteği karşılamak için kullanılır ve önbellekteki kopyayı değiştirir. Önbellekteki kopya sunucu kopyasıyla aynıysa, önbelleğe alınan kopya kullanılır. HTTP önbelleğe alma protokolünde bu, koşullu bir istek kullanılarak elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [\<requestCaching > öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
