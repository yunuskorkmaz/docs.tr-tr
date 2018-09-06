---
title: Eş Çözücüler
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 01320d98953c8fdc057aeec840ace4b818fcf115
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870064"
---
# <a name="peer-resolvers"></a>Eş Çözücüler
Bir kafesine bağlanmak için diğer düğümler IP adreslerini Eş düğüm gerektirir. IP adresleri, ağ kimliği alır ve bu belirli kafes kimliğe sahip kayıtlı düğümlere karşılık gelen adreslerinden oluşan bir liste döndürür Çözümleyicisi hizmeti iletişim kurarak elde edilir Çözümleyici ağ hizmetiyle kaydetmek her düğüm sağlayarak oluşturur kayıtlı adreslerinden oluşan bir liste tutar.  
  
 Hangi PeerResolver hizmeti aracılığıyla belirtebilirsiniz `Resolver` özelliği <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Desteklenen eş çözücüler  
 Eş kanal Çözümleyicileri iki tür destekler: Eş Adı Çözümleme Protokolü (PNRP) ve özel Çözücü Hizmetleri.  
  
 Varsayılan olarak, eş kanalı ağ içinde bulunmasına yönelik meslektaşlarınızla ve komşuları PNRP eş çözümleyici hizmetini kullanır. Durumlar/PNRP olduğu kullanılabilir ya da uygulanabilir platformlar için bir alternatif, sunucu tabanlı bulma hizmeti - Windows Communication Foundation (WCF) sağlar. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Uygulayan bir sınıf yazarak da açıkça bir özel Çözücü hizmet tanımlayabilirsiniz <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> arabirimi.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Eş Adı Çözümleme Protokolü'nü (PNRP)  
 PNRP, varsayılan çözümleyicisini [!INCLUDE[wv](../../../../includes/wv-md.md)], dağıtılmış, sunucusuz bir ad çözümleyici hizmet. PNRP de kullanılabilir üzerinde [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] Gelişmiş ağ paketi yükleyerek. Bunlar (örneğin, ilgili Kurumsal güvenlik duvarının eksikliği) belirli koşullara uyması şartıyla iki PNRP aynı sürümünü çalıştıran istemciler bu protokolü kullanarak birbirlerinin bulabilirsiniz. PNRP sürümü ile birlikte, Not [!INCLUDE[wv](../../../../includes/wv-md.md)] Gelişmiş ağ paketinde bulunan sürümden daha yeni. Microsoft Download Center PNRP için Güncelleştirmeleri denetle [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Özel Çözücü Hizmetleri  
 PNRP Hizmet kullanılamıyor veya kafes şekillendirme üzerinde tam denetim istiyorsanız, özel, sunucu tabanlı çözümleyicisini kullanabilirsiniz. Çözümleyici sınıfı yazarak bu hizmete açıkça tanımlayabilirsiniz uygulama <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> yerleşik varsayılan uygulama kullanarak veya arabirim <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 İstemci açıkça kaydı yenilenmemesi durumunda altında varsayılan uygulama hizmeti, istemci kayıtları bir belirli bir süre sonra süresi dolar. Kayıtları sürede başarıyla yenilemek için çözümleyicisini kullanarak istemcileri istemci-sunucu gecikme süresi üst sınırı farkında olması gerekir. Bu bir uygun yenileme zaman aşımı seçme içerir (`RefreshInterval`) çözümleyicisini üzerinde. (Daha fazla bilgi için [CustomPeerResolverService içinde: istemci kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Uygulama yazıcısı, ayrıca istemcileri ve özel Çözücü hizmet arasındaki bağlantıyı güvenli hale getirme dikkate almanız gerekir. Güvenlik ayarları kullanarak bunu yapabilirsiniz <xref:System.ServiceModel.NetTcpBinding> istemcileri çözümleyici hizmetiyle bağlantı kurmak için kullanın. Kimlik bilgilerini (kullanılıyorsa) üzerinde belirtmelisiniz `ChannelFactory` eş kanalı oluşturmak için kullanılır. Bu kimlik bilgileri geçirilen `ChannelFactory` özel Çözücü kanalları oluşturmak için kullanılır.  
  
> [!NOTE]
>  Yerel ve hazırlıksız ağlar ile özel bir çözümleyici kullanırken kullanarak veya bağlantı-yerel veya hazırlıksız ağlarını destekleyen uygulamalar bağlanırken kullanmak için tek bir bağlantı-yerel adresi seçer mantığı eklemek önerilir. Bu, birden çok bağlantı-yerel adresleri bilgisayarlarla olası nedeni Karışıklıktan engeller. Bu uygun olarak, eş kanalı yalnızca tek bir bağlantı-yerel adresi herhangi bir zamanda kullanılmasını destekler. Bu adresle belirtebilir `ListenIpAddress` özellikte <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Bir özel Çözücü uygulamak nasıl bir gösterimi için bkz. [eş kanalı özel eş Çözücü](https://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CustomPeerResolverService İçinde: İstemci Kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Eş Kanalı Güvenliği](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
