---
title: Eş Çözücüler
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: ef72f44a7dd7f3e8f3108e4f77dcdbdf8ef1b1b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554638"
---
# <a name="peer-resolvers"></a>Eş Çözücüler
Bir ağ bağlantısı için bir eş düğüm, diğer düğümlerin IP adreslerini gerektirir. IP adresleri bir çözümleyici hizmetiyle iletişim kurarak elde edilir ve bu da ağ KIMLIĞINI alır ve bu ağ KIMLIĞIYLE kaydedilen düğümlere karşılık gelen adreslerin bir listesini döndürür. Çözümleyici, bir kayıtlı adres listesini tutar ve bu, her bir düğümün hizmet ile kaydolmasına sahip tarafından oluşturduğu bir kayıt oluşturur.  
  
 Öğesinin özelliği aracılığıyla hangi PeerResolver hizmetini kullanacağınızı belirtebilirsiniz `Resolver` <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
## <a name="supported-peer-resolvers"></a>Desteklenen eş çözümleyiciler  
 Eş kanal iki tür çözümleyiciler destekler: eş adı çözümleme Protokolü (PNRP) ve özel çözümleyici Hizmetleri.  
  
 Eş kanal, varsayılan olarak, kafeste eşler ve komşuları bulmak için PNRP eş çözümleyici hizmetini kullanır. PNRP 'nin kullanılamadığı veya uygun olmadığı durumlar/platformlar için Windows Communication Foundation (WCF), sunucu tabanlı alternatif bir bulma hizmeti sağlar <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> . Ayrıca, arabirimini uygulayan bir sınıf yazarak özel bir çözümleyici hizmetini açık bir şekilde tanımlayabilirsiniz <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> .  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Eş adı çözümleme Protokolü (PNRP)  
 Windows Vista için varsayılan çözümleyici olan PNRP, dağıtılmış, sunucusuz bir ad çözümleyici hizmetidir. PNRP, Gelişmiş ağ paketi yüklenerek Windows XP SP2 üzerinde de kullanılabilir. Aynı PNRP sürümünü çalıştıran iki istemci, belirli koşulları (örneğin, Birleşik bir kurumsal güvenlik duvarının olmaması gibi) karşılamaları şartıyla, bu protokolü kullanarak birbirini da bulabilir. Windows Vista ile birlikte gelen PNRP sürümünün gelişmiş ağ paketine dahil olan sürümden daha yeni olduğunu unutmayın. Windows XP SP2 için PNRP güncelleştirmeleri için Microsoft Indirme Merkezi ' ne bakın.  
  
### <a name="custom-resolver-services"></a>Özel çözümleyici Hizmetleri  
 PNRP hizmeti kullanılamadığında veya ağ şekillendirme üzerinde tam denetim istediğinizde, özel, sunucu tabanlı bir çözümleyici hizmeti kullanabilirsiniz. Bu hizmeti, arabirimi uygulayan bir çözümleyici sınıfı yazarak <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> veya yerleşik varsayılan uygulamayı kullanarak açıkça tanımlayabilirsiniz <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> .  
  
 Hizmetin varsayılan uygulanması kapsamında, istemci kaydı açıkça yenilemezse, istemci kayıtlarının belirli bir süre sonunda süresi dolacak. Çözümleyici hizmetini kullanan istemciler, kayıtları zamanında başarıyla yenilemek için istemci-sunucu gecikme süresinin üst sınırının farkında olmalıdır. Bu, çözümleyici hizmetinde uygun yenileme zaman aşımını () seçmeyi içerir `RefreshInterval` . (Daha fazla bilgi için, bkz. [CustomPeerResolverService: Istemci kayıtları](inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Uygulama yazıcısının ayrıca istemciler ve özel çözümleyici Hizmeti arasındaki bağlantıyı güvenli hale getirmek de göz önünde bulundurmanız gerekir. Bunu, <xref:System.ServiceModel.NetTcpBinding> istemcilerin çözümleyici hizmetiyle iletişim kurmak için kullandığı güvenlik ayarlarını kullanarak yapabilirsiniz. Eş kanal oluşturmak için kullanılan (kullanılıyorsa) kimlik bilgilerini belirtmeniz gerekir `ChannelFactory` . Bu kimlik bilgileri, `ChannelFactory` özel çözümleyici için kanalları oluşturmak üzere kullanılan öğesine geçirilir.  
  
> [!NOTE]
> Özel bir çözümleyici ile yerel ve ımprompnetworks ağlarını kullanırken, bağlantı yerel veya impromptu ağlarını kullanan veya destekleyen uygulamaların, bağlanırken kullanılacak tek bir bağlantı yerel adresi seçen mantığı içermesi önemle tavsiye edilir. Bu, birden çok bağlantı yerel adresi olan bilgisayarlardan kaynaklanan karışıklıklara engel olur. Buna uygun olarak, eş kanal her seferinde yalnızca tek bir bağlantı yerel adresi kullanılmasını destekler. Bu adresi `ListenIpAddress` üzerinde özelliği ile belirtebilirsiniz <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
 Özel bir çözümleyici 'nin nasıl uygulanacağını gösteren bir gösterim için bkz. [eş kanal özel eş çözümleyici](/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CustomPeerResolverService İçinde: İstemci Kayıtları](inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Kavramları](peer-channel-concepts.md)
- [Eş Kanalı Güvenliği](peer-channel-security.md)
- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)
