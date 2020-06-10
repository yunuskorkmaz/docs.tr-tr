---
title: Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: d6018c8339cb04471bf9ce0f2ee86e091e1d1e95
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597533"
---
# <a name="configuring-system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
Bağlamalar bir uç noktaya konuşurken kullanılacak iletişim mekanizmasını belirtir ve bir uç noktaya nasıl bağlanılacağını gösterir. Bağlamalar, gerekli iletişim özelliklerini sağlamak üzere Windows Communication Foundation (WCF) kanallarının nasıl katmanlanmış olduğunu tanımlayan öğelerden oluşur. Bağlama üç tür öğe içerir:  
  
- Uç noktaya gönderilen iletilerle kullanılacak güvenlik, güvenilirlik, bağlam akışı ayarları veya Kullanıcı tanımlı protokolleri belirleyen protokol kanalı bağlama öğeleri.  
  
- Uç noktaya ileti gönderilirken kullanılacak temeldeki aktarım protokolünü belirleyen taşıma kanalı bağlama öğeleri (örneğin, TCP veya HTTP).  
  
- İleti kodlama bağlama öğeleri; Örneğin, metin/XML, ikili veya Ileti Iletimi Iyileştirme mekanizması (MTOM) gibi uç noktaya gönderilen iletilerde kullanılacak tel kodlamasını belirleyen ileti kodlaması.  
  
 Bu konu, sistem tarafından sunulan tüm Windows Communication Foundation (WCF) bağlamalarını gösterir. Bunlardan hiçbiri uygulamanız için tam gereksinimleri karşılamıyorsa, sınıfını kullanarak bir bağlama oluşturabilirsiniz <xref:System.ServiceModel.Channels.CustomBinding> . Özel Bağlamalar Oluşturma hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../extending/custom-bindings.md).  
  
> [!IMPORTANT]
> Güvenliği etkinleştirilmiş bir bağlama seçin. Varsayılan olarak, bağlama dışında tüm bağlamaların <xref:System.ServiceModel.BasicHttpBinding> güvenliği etkinleştirilmiştir. Güvenli bir bağlama seçmezseniz veya güvenliği devre dışı bıraktığınızda, ağ alışvertlarınızın güvenli bir veri merkezinde veya yalıtılmış bir ağda olması gibi başka bir şekilde korunduğundan emin olun.  
  
> [!IMPORTANT]
> Ağ değişimi başka bir yöntemle güvenli hale getirilmediği takdirde, güvenliği desteklemeyen veya güvenlik devre dışı olan bağlamalarla çift yönlü sözleşmeleri kullanmayın.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Aşağıdaki bağlamalar WCF ile birlikte gönderilir.  
  
|Bağlama|Yapılandırma öğesi|Açıklama|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|WS-Basic profiliyle uyumlu Web Hizmetleri, örneğin ASP.NET Web Services (ASMX) tabanlı hizmetler ile iletişim kurmak için uygun bir bağlama. Bu bağlama, varsayılan ileti kodlaması olarak aktarım ve metin/XML olarak HTTP kullanır.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|Çift yönlü hizmet sözleşmeleri için uygun olan güvenli ve birlikte çalışabilen bir bağlama.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../configure-apps/file-schema/wcf/ws2007httpbinding.md)|<xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession> Ve bağlama öğelerinin doğru sürümleri için destek sağlayan güvenli ve birlikte çalışabilen bir bağlama <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> .|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü hizmet sözleşmeleri veya SOAP aracıları üzerinden iletişim için uygun olan güvenli ve birlikte çalışabilen bir bağlama.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|WS-Federation protokolünü destekleyen güvenli ve birlikte çalışabilen bir bağlama, bir federasyonda olan kuruluşların, kullanıcıların kimliğini etkin bir şekilde doğrulamasına ve yetkilendirmesine olanak tanır.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|' Dan türetilen ve federe güvenliği destekleyen güvenli ve birlikte çalışabilen bir bağlama <xref:System.ServiceModel.WS2007HttpBinding> .|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|WCF uygulamaları arasında makineler arası iletişim için uygun, güvenli ve iyileştirilmiş bir bağlama.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md)|WCF uygulamaları arasındaki makineye yönelik iletişim için uygun olan güvenli, güvenilir ve iyileştirilmiş bir bağlama.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|WCF uygulamaları arasında çapraz makine iletişimi için uygun olan bir sıraya alınmış bağlama.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Güvenli, çok makineli iletişim sağlayan bir bağlama.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP iletileri yerine HTTP istekleri aracılığıyla kullanıma sunulan WCF Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Bir WCF uygulaması ile mevcut Message Queuing (MSMQ olarak da bilinir) uygulamaları arasında çapraz makine iletişimi için uygun bir bağlama.|  
  
## <a name="binding-features"></a>Bağlama özellikleri  
 Sonraki tabloda, sistem tarafından belirtilen bağlamaların her biri sunulan bazı temel özellikler gösterilmektedir. Bağlamalar ilk sütunda listelenir ve özelliklerle ilgili bilgiler tabloda açıklanmıştır. Aşağıdaki tabloda kullanılan bağlama kısaltmalarının bir anahtarı verilmiştir. Bir bağlama seçmek için, hangi sütunun ihtiyacınız olan tüm satır özelliklerini karşılayıp karşılamadığını belirleyin.  
  
|Bağlama|Birlikte çalışabilirlik|Güvenlik modu (varsayılan)|Oturum<br /><br /> (Varsayılan)|İşlemler|Çift Yönlü|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Temel profil 1,1|(Yok), aktarım, Ileti, karışık|Hiçbiri, (yok)|(Yok)|yok|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|None, Transport, (Ileti), karışık|(Yok), taşıma, güvenilir oturum|(Yok), Evet|yok|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|None, Transport, (Ileti), karışık|(Yok), taşıma, güvenilir oturum|(Yok), Evet|yok|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Hiçbiri, (Ileti)|(Güvenilir oturum)|(Yok), Evet|Yes|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Hiçbiri, (Ileti), karışık|(Yok), güvenilir oturum|(Yok), Evet|Hayır|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Hiçbiri, (Ileti), karışık|(Yok), güvenilir oturum|(Yok), Evet|Hayır|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Hiçbiri, (aktarım), Ileti,<br /><br /> Karışık|Güvenilir oturum, (aktarım)|(Yok), Evet|Yes|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Seçim<br /><br /> Aktarım|Hiçbiri, (taşıma)|(Yok), Evet|Yes|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Hiçbiri, Ileti, (taşıma), her Ikisi|(Yok)|(Yok), Evet|Hayır|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eşdüzey hizmet sağlayıcı|Hiçbiri, Ileti, (aktarım), karışık|(Yok)|(Yok)|Yes|  
|<xref:System.ServiceModel.WebHttpBinding>|.NET|None, Transport, TransportCredentialOnly|(Yok)|(Yok)|yok|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Hiçbiri, (taşıma)|(Yok)|(Yok), Evet|yok|  
  
 Aşağıdaki tabloda, önceki tabloda bulunan özellikler açıklanmaktadır.  
  
|Öne çıkan özelliği|Açıklama|  
|-------------|-----------------|  
|Birlikte çalışabilirlik türü|Bağlamanın birlikte çalışmasını sağlayan protokol veya teknolojiyi adlandırır.|  
|Güvenlik|Kanalın nasıl güvenli olduğunu belirtir:<br /><br /> -None: SOAP iletisi güvenli değil ve istemcinin kimliği doğrulanmadı.<br />-Taşıma: güvenlik gereksinimleri aktarım katmanında karşılanır.<br />-Message: güvenlik gereksinimleri ileti katmanında karşılanır.<br />-Mixed: Bu güvenlik modu olarak bilinir `TransportWithMessageCredentials` . İleti düzeyinde kimlik bilgilerini işler ve bütünlük ve gizlilik gereksinimleri aktarım katmanı tarafından karşılanır.<br />-Her ikisi: ileti düzeyi ve aktarım düzeyi güvenliği kullanılır. Bu özellik, için benzersizdir <xref:System.ServiceModel.NetMsmqBinding> .|  
|Oturum|Bu bağlamanın oturum sözleşmelerini destekleyip desteklemediğini belirtir.|  
|İşlemler|İşlemlerin etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|Çift Yönlü|Çift yönlü sözleşmelerin desteklenip desteklenmediğini belirtir. Bu özelliğin bağlamadaki oturumlar için destek gerektirdiğini göz önünde koşın.|  
|Akış|İleti akışının desteklenip desteklenmediğini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktası Oluşturma Genel Bakış](../endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../using-bindings-to-configure-services-and-clients.md)
- [Temel WCF Programlama](../basic-wcf-programming.md)
