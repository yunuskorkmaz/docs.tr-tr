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
ms.openlocfilehash: 594aef9feee81d026abd6313f1e75cb518479688
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499836"
---
# <a name="location-based-cache-policies"></a>Konum temelli önbellek ilkeleri
Konum temelli önbellek İlkesi burada istenen kaynak gelen gerçekleştirilebilecek göre geçerli önbelleğe alınan girişlerin güncellik tanımlar. Önbelleğe alınmış kaynak geçerli kullanan mevcut değilse sunucu tarafından belirtilen yeniden doğrulama gereksinimlerini ihlal etmemesini. Konum temelli önbellek İlkesi kullanılarak programlı olarak oluşturulmuş bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> sınıf oluşturucusu. Konum tabanlı ilke türünü oluşturucu kullanılarak geçirilen bir <xref:System.Net.Cache.RequestCacheLevel> veya <xref:System.Net.Cache.HttpRequestCacheLevel> numaralandırma değeri. Konum temelli önbellek ilkeleri oluşturma kod örnekleri için bkz. [nasıl yapılır: Uygulama için bir konum temelli önbellek İlkesi ayarlama](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). Köprü Metni Aktarım Protokolü (http ve https) kaynaklar için konum temelli önbellek İlkesi her türü aşağıdaki bölümlerde açıklanmaktadır.  
  
## <a name="cache-if-available-policy"></a>Varsa önbellek İlkesi  
 Geçerli bir istenen kaynak, yerel önbellek üzerinde ise, önbelleğe alınmış kaynak kullanılır; Aksi takdirde, istek için kaynak sunucuya gönderilir. İstenen kaynak, istemci ve sunucu arasında herhangi bir önbellekte kullanılabilir durumda, istek bir ara önbelleği tarafından karşılanamıyor.  
  
## <a name="cache-only-policy"></a>Tek önbellek İlkesi  
 Geçerli bir istenen kaynak, yerel önbellek üzerinde ise, önbelleğe alınmış kaynak kullanılır. Bu önbellek ilke düzeyi belirtildiğinde bir <xref:System.Net.WebException> öğe yerel önbellek üzerinde değilse, özel durum harekete geçirilir.  
  
## <a name="cache-or-next-cache-only-policy"></a>Önbelleğe alın ya da yalnızca ilke sonraki önbellek  
 Geçerli bir istenen kaynak yerel veya bir ara önbelleğe yerel ağda ise, önbelleğe alınmış kaynak kullanılır. Aksi takdirde, bir <xref:System.Net.WebException> özel durumu oluşturulur. HTTP protokolü önbelleğe alma, bu yalnızca-IF-önbelleğe alınmış önbellek denetimi yönergesi kullanarak elde edilir.  
  
## <a name="no-cache-no-store-policy"></a>Hiçbir önbellek Hayır Store İlkesi  
 İstenen kaynak, herhangi bir önbellekten kullanılmıyor ve hiçbir zaman herhangi bir önbellekte yerleştirilir. Yerel önbellek üzerinde istenen kaynak varsa kaldırılır. Bu ilke düzeyi için Ara önbellekler, bunlar da kaynak kaldırmalısınız gösterir. HTTP protokolü önbelleğe alma, mağaza içi önbellek denetimi yönergesi kullanarak sağlanır.  
  
## <a name="refresh-policy"></a>İlke yenileme  
 İstenen kaynak sunucudan alınan veya bir önbellek yerel önbellek dışında bulunan kullanılabilir. İstek bir ara önbelleği tarafından karşılanabileceğini önce söz konusu önbellek sunucusuyla önbelleğe alınmış girdisini düzeltin gerekir. HTTP protokolü önbelleğe alma, bu, max-age kullanılarak gerçekleştirilir = 0 önbellek denetimi yönergesi ve no-cache Pragma üstbilgisi.  
  
## <a name="reload-policy"></a>Yeniden yükleme İlkesi  
 İstenen kaynak sunucudan alınması gerekir. Yerel önbellek üzerinde yanıt kaydedilmiş olabilir. HTTP protokolü önbelleğe alma, no-cache önbellek denetimi yönergesi ve no-cache Pragma üstbilgisi kullanılarak sağlanır.  
  
## <a name="revalidate-policy"></a>İlke düzeltin  
 Kaynağın önbelleğinde kopyasını sunucudaki kopyayla karşılaştırır. Kopyanızı sunucudaki kopyayla yeniyse, isteği gerçekleştirmek için kullanılır ve önbelleğinde kopyasının yerini alır. Önbellekteki kopyayı sunucu kopyası ile aynı ise, önbelleğe alınmış kopyayı kullanılır. HTTP protokolü önbelleğe alma, koşullu isteği kullanılarak sağlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)
- [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
