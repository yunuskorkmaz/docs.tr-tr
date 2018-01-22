---
title: "Eş Çözücüler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79c26ca9e167455dfbd664ea96e574c130cdc3d2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="peer-resolvers"></a>Eş Çözücüler
Bir kafes bağlanmak için diğer düğümlere IP adreslerini Eş düğüm gerektirmez. IP adreslerini kafes kimliği alır ve bu belirli kafes kimliği ile kayıtlı düğümler için karşılık gelen adresleri listesi döndüren bir çözümleyici hizmeti ile iletişim kurarak elde edilir Çözümleyici hizmete kaydolmak her düğümünde kafes sağlayarak oluşturur kayıtlı adreslerinin bir listesini tutar.  
  
 Aracılığıyla hangi PeerResolver hizmet belirtebilirsiniz `Resolver` özelliği <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Desteklenen eş çözücüler  
 Eş kanal çözümleyiciler iki tür destekler: Eş Adı Çözümleme Protokolü (PNRP) ve özel Çözücü Hizmetleri.  
  
 Varsayılan olarak, eş kanalı kafes PNRP eş çözümleyicisini eşler ve komşuları bulma için kullanır. PNRP olduğu kullanılabilir veya uygun durumlarda/platformlar için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir alternatif, sunucu tabanlı bulma hizmeti - sağlar <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Uygulayan bir sınıf yazarak da açıkça özel çözümleyicisini tanımlayabilirsiniz <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> arabirimi.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Eş Adı Çözümleme Protokolü (PNRP)  
 PNRP, varsayılan çözümleyicisini [!INCLUDE[wv](../../../../includes/wv-md.md)], bir dağıtılmış, sunucusuz ad çözümleyici hizmetidir. PNRP de kullanılabilir üzerinde [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] Gelişmiş ağ paketi yükleyerek. Belirli koşullar (örneğin, ilgili Kurumsal güvenlik duvarı yetersizliği) karşıladıklarından sağlanan PNRP aynı sürümünü çalıştıran herhangi iki istemcileri birbirine bu protokolü kullanarak bulabilir. PNRP sürümü ile birlikte olduğunu unutmayın [!INCLUDE[wv](../../../../includes/wv-md.md)] Gelişmiş ağ paketinde bulunan sürümden daha yeni. Microsoft Download Center PNRP için Güncelleştirmeleri denetle [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Özel Çözücü Hizmetleri  
 PNRP Hizmet kullanılamıyor veya kafes şekillendirme üzerinde tam denetim istediğiniz zaman, sunucu tabanlı özel çözümleyicisini kullanabilirsiniz. Çözümleyici sınıfı yazarak bu hizmete açıkça tanımlayabilirsiniz uygulama <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> yerleşik varsayılan uygulamasını kullanarak veya arabirim <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 İstemci kayıt açıkça yenilemez varsa hizmetinin varsayılan uygulamada, istemci kayıtları belirli bir miktar süre sonra süresi dolacak. Yenileme zamanının başarılı bir şekilde kayıtlar için çözümleyicisini kullanarak istemcileri istemci-sunucu gecikme süresi üst sınırı farkında olmanız gerekir. Bu uygun yenileme zaman aşımı seçme içerir (`RefreshInterval`) çözümleyicisini üzerinde. (Daha fazla bilgi için bkz: [CustomPeerResolverService içinde: istemci kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Uygulama yazarı, aynı zamanda istemcileri ve özel Çözücü hizmeti arasındaki bağlantının güvenli hale getirme dikkate almanız gerekir. Güvenlik ayarları kullanarak bunu yapabilirsiniz <xref:System.ServiceModel.NetTcpBinding> istemcileri çözümleyicisini iletişim kurmak için kullanır. Kimlik bilgileri (kullanılıyorsa) üzerinde belirtmeniz gerekir `ChannelFactory` eş kanalı oluşturmak için kullanılır. Bu kimlik bilgileri geçirilen `ChannelFactory` özel çözümleyiciye kanallar oluşturmak için kullanılır.  
  
> [!NOTE]
>  Yerel ve hazırlıksız ağlar özel çözümleyici ile kullanırken, kullanarak veya bağlantı-yerel veya hazırlıksız ağı destekleyen uygulamalar bağlanırken kullanılacak tek bir bağlantı-yerel adresi seçer mantığı dahil önerilir. Bu, birden çok bağlantı-yerel adresleri bilgisayarlarla olası nedeni Karışıklıktan engeller. Buna uygun olarak, eş kanalı yalnızca tek bir bağlantı-yerel adresi herhangi bir zamanda kullanılmasını destekler. Bu adresle belirtebilir `ListenIpAddress` özelliği <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Özel Çözücü uygulamak nasıl tanıtımı için bkz: [eş kanalı özel eş çözümleyici](http://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CustomPeerResolverService İçinde: İstemci Kayıtları](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Eş Kanalı Güvenliği](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
