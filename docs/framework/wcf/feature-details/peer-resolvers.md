---
title: Eş Çözücüler
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 3bcdeffac3673c1c464a35d8b6e089efd7394907
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919236"
---
# <a name="peer-resolvers"></a>Eş Çözücüler
Bir ağ bağlantısı için bir eş düğüm, diğer düğümlerin IP adreslerini gerektirir. IP adresleri bir çözümleyici hizmetiyle iletişim kurarak elde edilir ve bu da ağ KIMLIĞINI alır ve bu ağ KIMLIĞIYLE kaydedilen düğümlere karşılık gelen adreslerin bir listesini döndürür. Çözümleyici, bir kayıtlı adres listesini tutar ve bu, her bir düğümün hizmet ile kaydolmasına sahip tarafından oluşturduğu bir kayıt oluşturur.  
  
 <xref:System.ServiceModel.NetPeerTcpBinding>`Resolver` özelliği aracılığıyla hangi PeerResolver hizmetini kullanacağınızı belirtebilirsiniz.  
  
## <a name="supported-peer-resolvers"></a>Desteklenen eş çözümleyiciler  
 Eş kanal iki tür çözümleyiciler destekler: eş adı çözümleme Protokolü (PNRP) ve özel çözümleyici Hizmetleri.  
  
 Eş kanal, varsayılan olarak, kafeste eşler ve komşuları bulmak için PNRP eş çözümleyici hizmetini kullanır. PNRP 'nin kullanılamadığı veya uygun olmadığı durumlar/platformlar için Windows Communication Foundation (WCF), <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>alternatif, sunucu tabanlı bulma hizmeti sağlar. Ayrıca, <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> arabirimini uygulayan bir sınıf yazarak özel bir çözümleyici hizmetini açık bir şekilde tanımlayabilirsiniz.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Eş adı çözümleme Protokolü (PNRP)  
 Windows Vista için varsayılan çözümleyici olan PNRP, dağıtılmış, sunucusuz bir ad çözümleyici hizmetidir. PNRP, Gelişmiş ağ paketi yüklenerek Windows XP SP2 üzerinde de kullanılabilir. Aynı PNRP sürümünü çalıştıran iki istemci, belirli koşulları (örneğin, Birleşik bir kurumsal güvenlik duvarının olmaması gibi) karşılamaları şartıyla, bu protokolü kullanarak birbirini da bulabilir. Windows Vista ile birlikte gelen PNRP sürümünün gelişmiş ağ paketine dahil olan sürümden daha yeni olduğunu unutmayın. Windows XP SP2 için PNRP güncelleştirmeleri için Microsoft Indirme Merkezi ' ne bakın.  
  
### <a name="custom-resolver-services"></a>Özel çözümleyici Hizmetleri  
 PNRP hizmeti kullanılamadığında veya ağ şekillendirme üzerinde tam denetim istediğinizde, özel, sunucu tabanlı bir çözümleyici hizmeti kullanabilirsiniz. Bu hizmeti, <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> arabirimini uygulayan bir çözümleyici sınıfı yazarak veya yerleşik varsayılan uygulama olan <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>kullanarak açıkça tanımlayabilirsiniz.  
  
 Hizmetin varsayılan uygulanması kapsamında, istemci kaydı açıkça yenilemezse, istemci kayıtlarının belirli bir süre sonunda süresi dolacak. Çözümleyici hizmetini kullanan istemciler, kayıtları zamanında başarıyla yenilemek için istemci-sunucu gecikme süresinin üst sınırının farkında olmalıdır. Bu, çözümleyici hizmetinde uygun yenileme zaman aşımını (`RefreshInterval`) seçmeyi içerir. (Daha fazla bilgi için, bkz. [CustomPeerResolverService: Istemci kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Uygulama yazıcısının ayrıca istemciler ve özel çözümleyici Hizmeti arasındaki bağlantıyı güvenli hale getirmek de göz önünde bulundurmanız gerekir. Bunu, istemcilerin çözümleyici hizmetiyle iletişim kurmak için kullandığı <xref:System.ServiceModel.NetTcpBinding> güvenlik ayarlarını kullanarak yapabilirsiniz. Eş kanal oluşturmak için kullanılan `ChannelFactory` (kullanılıyorsa) kimlik bilgilerini belirtmeniz gerekir. Bu kimlik bilgileri, özel çözümleyici 'de kanal oluşturmak için kullanılan `ChannelFactory` geçirilir.  
  
> [!NOTE]
> Özel bir çözümleyici ile yerel ve ımprompnetworks ağlarını kullanırken, bağlantı yerel veya impromptu ağlarını kullanan veya destekleyen uygulamaların, bağlanırken kullanılacak tek bir bağlantı yerel adresi seçen mantığı içermesi önemle tavsiye edilir. Bu, birden çok bağlantı yerel adresi olan bilgisayarlardan kaynaklanan karışıklıklara engel olur. Buna uygun olarak, eş kanal her seferinde yalnızca tek bir bağlantı yerel adresi kullanılmasını destekler. Bu adresi <xref:System.ServiceModel.NetPeerTcpBinding>`ListenIpAddress` özelliği ile belirtebilirsiniz.  
  
 Özel bir çözümleyici 'nin nasıl uygulanacağını gösteren bir gösterim için bkz. [eş kanal özel eş çözümleyici](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CustomPeerResolverService İçinde: İstemci Kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Eş Kanalı Güvenliği](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
