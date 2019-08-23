---
title: Eş Çözücüler
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 0547bb37b03235c61f43cec365551438f7931ad1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909921"
---
# <a name="peer-resolvers"></a>Eş Çözücüler
Bir ağ bağlantısı için bir eş düğüm, diğer düğümlerin IP adreslerini gerektirir. IP adresleri bir çözümleyici hizmetiyle iletişim kurarak elde edilir ve bu da ağ KIMLIĞINI alır ve bu ağ KIMLIĞIYLE kaydedilen düğümlere karşılık gelen adreslerin bir listesini döndürür. Çözümleyici, bir kayıtlı adres listesini tutar ve bu, her bir düğümün hizmet ile kaydolmasına sahip tarafından oluşturduğu bir kayıt oluşturur.  
  
 Öğesinin özelliği`Resolver` aracılığıyla hangi PeerResolver hizmetini kullanacağınızı belirtebilirsiniz. <xref:System.ServiceModel.NetPeerTcpBinding>  
  
## <a name="supported-peer-resolvers"></a>Desteklenen eş çözümleyiciler  
 Eş kanal iki tür çözümleyiciler destekler: Eş adı çözümleme Protokolü (PNRP) ve özel çözümleyici Hizmetleri.  
  
 Eş kanal, varsayılan olarak, kafeste eşler ve komşuları bulmak için PNRP eş çözümleyici hizmetini kullanır. PNRP 'nin kullanılamadığı veya uygun olmadığı durumlar/platformlar için Windows Communication Foundation (WCF), sunucu tabanlı alternatif bir bulma hizmeti <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>sağlar. Ayrıca, <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> arabirimini uygulayan bir sınıf yazarak özel bir çözümleyici hizmetini açık bir şekilde tanımlayabilirsiniz.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Eş adı çözümleme Protokolü (PNRP)  
 İçin [!INCLUDE[wv](../../../../includes/wv-md.md)]varsayılan çözümleyici olan PNRP, dağıtılmış, sunucusuz bir ad çözümleyici hizmetidir. PNRP, Gelişmiş ağ paketi yüklenerek [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] üzerinde de kullanılabilir. Aynı PNRP sürümünü çalıştıran iki istemci, belirli koşulları (örneğin, Birleşik bir kurumsal güvenlik duvarının olmaması gibi) karşılamaları şartıyla, bu protokolü kullanarak birbirini da bulabilir. İle [!INCLUDE[wv](../../../../includes/wv-md.md)] birlikte gelen PNRP sürümünün gelişmiş ağ paketine dahil olan sürümden daha yeni olduğunu unutmayın. İçin [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]PNRP güncelleştirmeleri Için Microsoft İndirme Merkezi ' ne bakın.  
  
### <a name="custom-resolver-services"></a>Özel çözümleyici Hizmetleri  
 PNRP hizmeti kullanılamadığında veya ağ şekillendirme üzerinde tam denetim istediğinizde, özel, sunucu tabanlı bir çözümleyici hizmeti kullanabilirsiniz. Bu hizmeti, <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> arabirimi uygulayan bir çözümleyici sınıfı yazarak veya yerleşik varsayılan <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>uygulamayı kullanarak açıkça tanımlayabilirsiniz.  
  
 Hizmetin varsayılan uygulanması kapsamında, istemci kaydı açıkça yenilemezse, istemci kayıtlarının belirli bir süre sonunda süresi dolacak. Çözümleyici hizmetini kullanan istemciler, kayıtları zamanında başarıyla yenilemek için istemci-sunucu gecikme süresinin üst sınırının farkında olmalıdır. Bu, çözümleyici hizmetinde uygun yenileme zaman aşımını (`RefreshInterval`) seçmeyi içerir. (Daha fazla bilgi için, [bkz. CustomPeerResolverService içinde: İstemci kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Uygulama yazıcısının ayrıca istemciler ve özel çözümleyici Hizmeti arasındaki bağlantıyı güvenli hale getirmek de göz önünde bulundurmanız gerekir. Bunu, <xref:System.ServiceModel.NetTcpBinding> istemcilerin çözümleyici hizmetiyle iletişim kurmak için kullandığı güvenlik ayarlarını kullanarak yapabilirsiniz. Eş kanal oluşturmak için `ChannelFactory` kullanılan (kullanılıyorsa) kimlik bilgilerini belirtmeniz gerekir. Bu kimlik bilgileri, özel çözümleyici `ChannelFactory` için kanalları oluşturmak üzere kullanılan öğesine geçirilir.  
  
> [!NOTE]
> Özel bir çözümleyici ile yerel ve ımprompnetworks ağlarını kullanırken, bağlantı yerel veya impromptu ağlarını kullanan veya destekleyen uygulamaların, bağlanırken kullanılacak tek bir bağlantı yerel adresi seçen mantığı içermesi önemle tavsiye edilir. Bu, birden çok bağlantı yerel adresi olan bilgisayarlardan kaynaklanan karışıklıklara engel olur. Buna uygun olarak, eş kanal her seferinde yalnızca tek bir bağlantı yerel adresi kullanılmasını destekler. Bu adresi `ListenIpAddress` <xref:System.ServiceModel.NetPeerTcpBinding>üzerinde özelliği ile belirtebilirsiniz.  
  
 Özel bir çözümleyici 'nin nasıl uygulanacağını gösteren bir gösterim için bkz. [eş kanal özel eş çözümleyici](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CustomPeerResolverService içinde: İstemci kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Eş Kanalı Güvenliği](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
