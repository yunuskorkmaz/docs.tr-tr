---
title: Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: 184f4da26df2c688b2b6f30f063bab058af37a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
Bağlamalar ve bir bitiş noktasına bağlanmak nasıl belirtmek için bir uç nokta konuşurken kullanmak için iletişim mekanizması belirtin. Bağlamaları nasıl Windows Communication Foundation (WCF) kanalları yedeklemek için gerekli iletişim özelliklerini sağlamak için katmanlı tanımlama öğelerden oluşur. Bağlama öğeleri üç tür içerir:  
  
-   Güvenlik, güvenilirlik, içeriği akış ayarları veya kullanıcı tanımlı protokolleri uç noktasına gönderilen iletileri ile birlikte kullanmak için belirleyen Protokolü kanal bağlama öğeleri.  
  
-   Uç nokta için örneğin, TCP veya HTTP iletileri gönderirken kullanmak için temel Aktarım Protokolü belirlemek kanal bağlama öğelerini taşıma.  
  
-   Kablo text/XML, ikili, örneğin, uç noktasına gönderilen iletiler için kullanılacak kodlamayı bağlama öğeleri kodlama ileti veya ileti iletim en iyi duruma getirme mekanizmasını (MTOM).  
  
 Bu konuda tüm sistem tarafından sağlanan Windows Communication Foundation (WCF) bağlamalar sunulmaktadır. Hiçbiri, uygulamanız için tam gereksinimleri karşılıyorsa, kullanarak bir bağlama oluşturabilirsiniz <xref:System.ServiceModel.Channels.CustomBinding> sınıfı. Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Güvenliği etkinleştirilmiş sahip bir bağlama seçin. Varsayılan olarak, tüm bağlamaları dışında <xref:System.ServiceModel.BasicHttpBinding> bağlama, güvenliği etkinleştirilmiş olması. Güvenli bağlama seçmezseniz veya güvenlik devre dışı bırakırsanız, ağ iletişimlerini güvenli veri merkezinde veya yalıtılmış bir ağda olması gibi bazı diğer şekilde, korunan emin olun.  
  
> [!IMPORTANT]
>  Çift yönlü sözleşmeler güvenlik desteklemez veya başka bir şekilde ağ exchange güvenli sürece devre dışı, güvenlik sahip bağlamalarla kullanmayın.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Aşağıdaki bağlamaları WCF ile aktarılır.  
  
|Bağlama|Yapılandırma öğesi|Açıklama|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|WS-temel profil uyumluluğunu Web Hizmetleri ile Örneğin, ASP.NET Web Hizmetleri (ASMX) iletişim kurmak için uygun olan bir bağlama-services tabanlı. Bu bağlama taşıma ve varsayılan ileti kodlama olarak text/XML olarak HTTP kullanır.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Olmayan yönlü Hizmet sözleşmeleri için uygun bir güvenli ve birlikte çalışabilir bağlama.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Doğru sürümleri için destek sağlayan bir güvenli ve birlikte çalışabilir bağlama <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğeleri.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli ve birlikte çalışabilir bağlama.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Güvenli ve birlikte çalışabilir, bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların etkinleştirme WS-Federasyon protokolünü destekler.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Türetilen bir güvenli ve birlikte çalışabilir bağlama <xref:System.ServiceModel.WS2007HttpBinding> ve Federasyon güvenlik destekler.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Güvenli ve en iyi duruma getirilmiş bağlama WCF uygulamalar arasında makineler arası iletişim için uygundur.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Makine üzerindeki WCF uygulamaları arasındaki iletişim için uygun bir güvenli, güvenilir ve en iyi duruma getirilmiş bağlama.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Sıraya alınan bir bağlama WCF uygulamalar arasında makineler arası iletişim için uygundur.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Güvenli, çok makineli iletişimi sağlayan bir bağlama.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP iletilerine yerine HTTP istekleri aracılığıyla kullanıma sunulan WCF Web hizmeti için uç noktalar yapılandırmak için kullanılan bir bağlama.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Bir bağlama WCF uygulaması ve var olan Message Queuing (MSMQ olarak da bilinir) arasındaki makineler arası iletişim için uygun olan uygulamalar.|  
  
## <a name="binding-features"></a>Bağlama özellikleri  
 Sonraki tabloda önemli özelliklerinden bazıları her sağlanan sistem tarafından sağlanan bağlamalar gösterir. Bağlamaları ilk sütununda listelenir ve özellikleri ile ilgili bilgiler tabloda açıklanmıştır. Aşağıdaki tabloda kullanılan bağlama kısaltmalar için bir anahtar sağlar. Bir bağlama seçmek için gereksinim duyduğunuz satır özelliklerin tümü, hangi sütunun karşılayan belirler.  
  
|Bağlama|Birlikte Çalışabilirlik|Mod güvenlik (varsayılan)|Oturum<br /><br /> (Varsayılan)|İşlemler|Çift Yönlü|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Temel Profil 1.1|(Hiçbiri), Aktarım, ileti, karma|None, (yok)|(Hiçbiri)|yok|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|None, taşıma (ileti), karma|(Hiçbiri), Aktarım, güvenilir oturum|(Hiçbiri), Evet|yok|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-güvenlik, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|None, taşıma (ileti), karma|(Hiçbiri), Aktarım, güvenilir oturum|(Hiçbiri), Evet|yok|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Hiçbiri (ileti)|(Güvenilir oturum)|(Hiçbiri), Evet|Evet|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federasyon|Hiçbiri (ileti), karma|(Hiçbiri), güvenli oturum|(Hiçbiri), Evet|Hayır|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federasyon|Hiçbiri (ileti), karma|(Hiçbiri), güvenli oturum|(Hiçbiri), Evet|Hayır|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Hiçbiri (aktarım) ileti,<br /><br /> Karma|Güvenilir oturum, (aktarım)|(Hiçbiri), Evet|Evet|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|None,<br /><br /> (Aktarım)|Hiçbiri (aktarım)|(Hiçbiri), Evet|Evet|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|None, iletiyi (aktarım), her ikisi|(Hiçbiri)|(Hiçbiri), Evet|Hayır|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eş|None, iletiyi (aktarım), karma|(Hiçbiri)|(Hiçbiri)|Evet|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Hiçbiri (aktarım)|(Hiçbiri)|(Hiçbiri), Evet|yok|  
  
 Aşağıdaki tabloda önceki tabloda bulunan özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|  
|-------------|-----------------|  
|Birlikte çalışabilirlik türü|Adları protokolü veya teknolojisi ile birlikte çalışma bağlama sağlar.|  
|Güvenlik|Kanal güvenliği nasıl belirtir:<br /><br /> -Hiçbiri: SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.<br />-Taşıma: Güvenlik gereksinimlerini aktarım katmanında karşılanır.<br />-İleti: Güvenlik gereksinimlerini ileti katmanında karşılanır.<br />-Karma: Bu güvenlik modu olarak bilinir `TransportWithMessageCredentials`. Kimlik bilgileri ileti düzeyinde işler ve bütünlüğü ve gizliliği gereksinimleri Aktarım katmanı tarafından karşılanır.<br />-Her ikisi: Her iki ileti düzeyi ve aktarım düzeyi güvenlik kullanılır. Bu özellik için benzersiz olan <xref:System.ServiceModel.NetMsmqBinding>.|  
|Oturum|Bu bağlama oturum sözleşmeleri destekleyip desteklemediğini belirtir.|  
|İşlemler|İşlemler etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|Çift Yönlü|Çift yönlü sözleşmeler desteklenip desteklenmediğini belirtir. Bu özellik destek oturumlarının bağlamasında gerektirir unutmayın.|  
|Akış|İleti akış desteklenip desteklenmediğini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
