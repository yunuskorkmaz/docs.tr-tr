---
title: Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: c2c1f468fba404768fe01e84260125843964fea0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949619"
---
# <a name="configuring-system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
Bağlamalar bir uç noktaya konuşurken kullanılacak iletişim mekanizmasını belirtir ve bir uç noktaya nasıl bağlanılacağını gösterir. Bağlamalar, gerekli iletişim özelliklerini sağlamak üzere Windows Communication Foundation (WCF) kanallarının nasıl katmanlanmış olduğunu tanımlayan öğelerden oluşur. Bağlama üç tür öğe içerir:  
  
- Uç noktaya gönderilen iletilerle kullanılacak güvenlik, güvenilirlik, bağlam akışı ayarları veya Kullanıcı tanımlı protokolleri belirleyen protokol kanalı bağlama öğeleri.  
  
- Uç noktaya ileti gönderilirken kullanılacak temeldeki aktarım protokolünü belirleyen taşıma kanalı bağlama öğeleri (örneğin, TCP veya HTTP).  
  
- İleti kodlama bağlama öğeleri; Örneğin, metin/XML, ikili veya Ileti Iletimi Iyileştirme mekanizması (MTOM) gibi uç noktaya gönderilen iletilerde kullanılacak tel kodlamasını belirleyen ileti kodlaması.  
  
 Bu konu, sistem tarafından sunulan tüm Windows Communication Foundation (WCF) bağlamalarını gösterir. Bunlardan hiçbiri uygulamanız için tam gereksinimleri karşılamıyorsa, <xref:System.ServiceModel.Channels.CustomBinding> sınıfını kullanarak bir bağlama oluşturabilirsiniz. Özel Bağlamalar Oluşturma hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
> Güvenliği etkinleştirilmiş bir bağlama seçin. Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> bağlama dışında tüm bağlamaların güvenliği etkinleştirilmiştir. Güvenli bir bağlama seçmezseniz veya güvenliği devre dışı bıraktığınızda, ağ alışvertlarınızın güvenli bir veri merkezinde veya yalıtılmış bir ağda olması gibi başka bir şekilde korunduğundan emin olun.  
  
> [!IMPORTANT]
> Ağ değişimi başka bir yöntemle güvenli hale getirilmediği takdirde, güvenliği desteklemeyen veya güvenlik devre dışı olan bağlamalarla çift yönlü sözleşmeleri kullanmayın.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Aşağıdaki bağlamalar WCF ile birlikte gönderilir.  
  
|Bağlama|Yapılandırma öğesi|Açıklama|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|WS-Basic profiliyle uyumlu Web Hizmetleri, örneğin ASP.NET Web Services (ASMX) tabanlı hizmetler ile iletişim kurmak için uygun bir bağlama. Bu bağlama, varsayılan ileti kodlaması olarak aktarım ve metin/XML olarak HTTP kullanır.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Çift yönlü hizmet sözleşmeleri için uygun olan güvenli ve birlikte çalışabilen bir bağlama.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<xref:System.ServiceModel.WSHttpBinding.Security%2A> ,<xref:System.ServiceModel.ReliableSession>Ve bağlama<xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> öğelerinin doğru sürümleri için destek sağlayan güvenli ve birlikte çalışabilen bir bağlama.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü hizmet sözleşmeleri veya SOAP aracıları üzerinden iletişim için uygun olan güvenli ve birlikte çalışabilen bir bağlama.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|WS-Federation protokolünü destekleyen güvenli ve birlikte çalışabilen bir bağlama, bir federasyonda olan kuruluşların, kullanıcıların kimliğini etkin bir şekilde doğrulamasına ve yetkilendirmesine olanak tanır.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|' Dan <xref:System.ServiceModel.WS2007HttpBinding> türetilen ve federe güvenliği destekleyen güvenli ve birlikte çalışabilen bir bağlama.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|WCF uygulamaları arasında makineler arası iletişim için uygun, güvenli ve iyileştirilmiş bir bağlama.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|WCF uygulamaları arasındaki makineye yönelik iletişim için uygun olan güvenli, güvenilir ve iyileştirilmiş bir bağlama.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|WCF uygulamaları arasında çapraz makine iletişimi için uygun olan bir sıraya alınmış bağlama.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Güvenli, çok makineli iletişim sağlayan bir bağlama.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP iletileri yerine HTTP istekleri aracılığıyla kullanıma sunulan WCF Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Bir WCF uygulaması ile mevcut Message Queuing (MSMQ olarak da bilinir) uygulamaları arasında çapraz makine iletişimi için uygun bir bağlama.|  
  
## <a name="binding-features"></a>Bağlama özellikleri  
 Sonraki tabloda, sistem tarafından belirtilen bağlamaların her biri sunulan bazı temel özellikler gösterilmektedir. Bağlamalar ilk sütunda listelenir ve özelliklerle ilgili bilgiler tabloda açıklanmıştır. Aşağıdaki tabloda kullanılan bağlama kısaltmalarının bir anahtarı verilmiştir. Bir bağlama seçmek için, hangi sütunun ihtiyacınız olan tüm satır özelliklerini karşılayıp karşılamadığını belirleyin.  
  
|Bağlama|Birlikte Çalışabilirlik|Güvenlik modu (varsayılan)|Oturum<br /><br /> (Varsayılan)|İşlemler|Çift Yönlü|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Temel profil 1,1|(Yok), aktarım, Ileti, karışık|Hiçbiri, (yok)|Seçim|yok|  
|<xref:System.ServiceModel.WSHttpBinding>|RW|None, Transport, (Ileti), karışık|(Yok), taşıma, güvenilir oturum|(Yok), Evet|yok|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|None, Transport, (Ileti), karışık|(Yok), taşıma, güvenilir oturum|(Yok), Evet|yok|  
|<xref:System.ServiceModel.WSDualHttpBinding>|RW|Hiçbiri, (Ileti)|(Güvenilir oturum)|(Yok), Evet|Evet|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Hiçbiri, (Ileti), karışık|(Yok), güvenilir oturum|(Yok), Evet|Hayır|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Hiçbiri, (Ileti), karışık|(Yok), güvenilir oturum|(Yok), Evet|Hayır|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Hiçbiri, (aktarım), Ileti,<br /><br /> Ilır|Güvenilir oturum, (aktarım)|(Yok), Evet|Evet|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Seçim<br /><br /> Aktarım|Hiçbiri, (taşıma)|(Yok), Evet|Evet|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Hiçbiri, Ileti, (taşıma), her Ikisi|Seçim|(Yok), Evet|Hayır|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eş|Hiçbiri, Ileti, (aktarım), karışık|Seçim|Seçim|Evet|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|None, Transport, TransportCredentialOnly|Seçim|Seçim|yok|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Hiçbiri, (taşıma)|Seçim|(Yok), Evet|yok|  
  
 Aşağıdaki tabloda, önceki tabloda bulunan özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|  
|-------------|-----------------|  
|Birlikte çalışabilirlik türü|Bağlamanın birlikte çalışmasını sağlayan protokol veya teknolojiyi adlandırır.|  
|Güvenlik|Kanalın nasıl güvenli olduğunu belirtir:<br /><br /> Seçim SOAP iletisi güvenli değil ve istemcinin kimliği doğrulanmadı.<br />Aktarım Güvenlik gereksinimleri aktarım katmanında karşılanır.<br />Mesaj Güvenlik gereksinimleri ileti katmanında karşılanır.<br />Ilır Bu güvenlik modu olarak `TransportWithMessageCredentials`bilinir. İleti düzeyinde kimlik bilgilerini işler ve bütünlük ve gizlilik gereksinimleri aktarım katmanı tarafından karşılanır.<br />İs İleti düzeyi ve aktarım düzeyi güvenliği kullanılır. Bu özellik, <xref:System.ServiceModel.NetMsmqBinding>için benzersizdir.|  
|Oturum|Bu bağlamanın oturum sözleşmelerini destekleyip desteklemediğini belirtir.|  
|İşlemler|İşlemlerin etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|Çift Yönlü|Çift yönlü sözleşmelerin desteklenip desteklenmediğini belirtir. Bu özelliğin bağlamadaki oturumlar için destek gerektirdiğini göz önünde koşın.|  
|Akış|İleti akışının desteklenip desteklenmediğini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
