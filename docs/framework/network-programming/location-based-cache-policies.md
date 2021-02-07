---
description: 'Daha fazla bilgi edinin: Location-Based önbellek Ilkeleri'
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
ms.openlocfilehash: ef770b45f173fee66c80d721766a0be6244bbeb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662721"
---
# <a name="location-based-cache-policies"></a>Konum Temelli Önbellek İlkeleri

Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alarak geçerli önbelleğe alınmış girişlerin yeniliği tanımlar. Önbelleğe alınmış bir kaynak, kullanılması durumunda sunucu tarafından belirtilen yeniden doğrulama gereksinimlerini ihlal etmezse geçerli olur. Konum tabanlı önbellek ilkesi, <xref:System.Net.Cache.RequestCachePolicy> veya sınıf oluşturucusu kullanılarak programlı bir şekilde oluşturulur <xref:System.Net.Cache.HttpRequestCachePolicy> . Konum tabanlı ilke türü, bir <xref:System.Net.Cache.RequestCacheLevel> veya numaralandırma değeri kullanılarak oluşturucuya geçirilir <xref:System.Net.Cache.HttpRequestCacheLevel> . Konum tabanlı önbellek ilkeleri oluşturan kod örnekleri için bkz. [nasıl yapılır: bir uygulama için Location-Based önbellek Ilkesi ayarlama](how-to-set-a-location-based-cache-policy-for-an-application.md). Aşağıdaki bölümlerde, Köprü Metni Aktarım Protokolü (http ve https) kaynakları için her konum tabanlı önbellek ilkesi türü açıklanmaktadır.  
  
## <a name="cache-if-available-policy"></a>Kullanılabilir Ilke varsa önbelleğe al  

 Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır; Aksi takdirde, kaynak isteği sunucuya gönderilir. İstenen kaynak, istemci ve sunucu arasındaki herhangi bir önbellekte kullanılabiliyorsa, istek bir ara önbellek tarafından karşılanabilir.  
  
## <a name="cache-only-policy"></a>Yalnızca önbellek Ilkesi  

 Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır. Bu önbellek ilkesi düzeyi belirtildiğinde, <xref:System.Net.WebException> öğe yerel önbellekte değilse bir özel durum oluşturulur.  
  
## <a name="cache-or-next-cache-only-policy"></a>Yalnızca önbellek veya sonraki önbellek Ilkesi  

 Geçerli bir istenen kaynak yerel önbellekte veya yerel alan ağı üzerindeki ara önbellekte ise, önbelleğe alınmış kaynak kullanılır. Aksi takdirde, bir <xref:System.Net.WebException> özel durum oluşturulur. HTTP önbelleğe alma protokolünde, bu, tek-if-önbelleğe alınmış önbellek denetim yönergesi kullanılarak elde edilir.  
  
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
- [\<requestCaching> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
