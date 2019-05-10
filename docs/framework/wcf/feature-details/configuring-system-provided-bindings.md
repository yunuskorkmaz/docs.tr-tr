---
title: Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: 49aacdc7db6bc9e8b951f69bcd880835bb9182f2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654518"
---
# <a name="configuring-system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
Bir uç noktaya konuşurken kullanın ve bir uç noktaya bağlanmak nasıl göstermek için iletişim mekanizması bağlantılarını belirtin. Bağlamaları nasıl Windows Communication Foundation (WCF) kanalları yukarı gerekli iletişime özellikleri katmanlıdır tanımlayan öğeleri oluşur. Bir bağlama üç öğe türleri içerir:  
  
- Güvenlik, güvenilirlik, içerik akışı ayarlarında veya kullanıcı tanımlı protokolleri uç noktasına gönderilen iletileri ile kullanılacak belirleyen Protokolü kanal bağlama öğeleri.  
  
- Uç noktaya, örneğin, TCP veya HTTP iletileri gönderirken kullanılacak temel alınan Aktarım Protokolü belirlemek kanal bağlama öğeleri taşıma.  
  
- İleti kablo uç noktaya, örneğin, gönderilen iletiler için metin/XML, ikili, kullanılacak kodlamayı bağlama öğeleri, kodlama veya ileti aktarım en iyi duruma getirme mekanizması (MTOM).  
  
 Bu konuda, tüm sistem tarafından sağlanan Windows Communication Foundation (WCF) bağlamaları sunulmaktadır. Bunlardan hiçbiri uygulamanız için tam gereksinimleri karşılıyorsa, kullanarak bir bağlama oluşturabilirsiniz <xref:System.ServiceModel.Channels.CustomBinding> sınıfı. Özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Güvenliği etkinleştirilmiş olan bir bağlama'ı seçin. Varsayılan olarak, tüm bağlamaları dışında <xref:System.ServiceModel.BasicHttpBinding> bağlama, güvenliği etkinleştirilmiş olması. Güvenli bir bağlama belirlemezseniz veya güvenlik devre dışı bırakırsanız, ağ iletişimlerini güvenli veri merkezinde veya yalıtılmış bir ağda gibi başka bir yolla, korunan emin olun.  
  
> [!IMPORTANT]
>  Çift yönlü sözleşmeler, güvenlik desteklemez veya ağ exchange bazı başka yollarla güvenli hale getirilmiş sürece güvenlik devre dışı olan bağlamaları ile kullanmayın.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Aşağıdaki bağlamaları WCF ile gönderilir.  
  
|Bağlama|Yapılandırma öğesi|Açıklama|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|WS-temel profil uyumlu Web Hizmetleri ile Örneğin, ASP.NET Web hizmetlerini (ASMX) iletişim kurmak için uygun bir bağlama-tabanlı hizmetler. Bu bağlama taşıma ve metin/XML ileti kodlama varsayılan olarak HTTP kullanır.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Uygun olmayan yönlü Hizmet sözleşmeleri için güvenli ve birlikte çalışabilen bağlama.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Doğru sürümleri için destek sağlayan güvenli ve birlikte çalışabilen bağlama <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğeleri.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü Hizmet sözleşmeleri veya SOAP aracıları üzerinden haberleşme için uygun olan güvenli ve birlikte çalışabilen bağlama.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Bir güvenli ve birlikte çalışabilen bağlama verimli bir şekilde kimliğini doğrulamak ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların etkinleştirme WS-Federasyon protokolünü destekler.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Türetilen bir güvenli ve birlikte çalışabilen bağlama <xref:System.ServiceModel.WS2007HttpBinding> ve birleşik güvenliği destekler.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Bir güvenli ve en iyi duruma getirilmiş bağlama WCF uygulamalar arasında çapraz makine haberleşmesi için uygundur.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Makinede, WCF uygulamalar arasında iletişim için uygun olan güvenli, güvenilir ve iyileştirilmiş bir bağlama.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Sıraya alınan bir bağlama WCF uygulamalar arasında çapraz makine haberleşmesi için uygundur.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Güvenli, çok makineli iletişimi sağlayan bir bağlama.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP iletileri yerine HTTP istekleri aracılığıyla kullanıma sunulan WCF Web Hizmetleri için uç noktası yapılandırmak için kullanılan bir bağlama.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|WCF uygulaması ve mevcut Message Queuing (MSMQ olarak da bilinir) arasında çapraz makine haberleşmesi için uygun bir bağlama uygulamalar.|  
  
## <a name="binding-features"></a>Bağlama özellikleri  
 Sonraki tabloda anahtar özelliklerinden bazıları her sağlanan sistem tarafından sağlanan bağlamalar gösterir. Bağlamaları ilk sütunda listelenir ve özellikleri ile ilgili bilgileri tabloda açıklanmıştır. Aşağıdaki tabloda kullanılan bağlama kısaltmalar için bir anahtar sağlar. Bir bağlama seçmek için hangi sütunun ihtiyacınız satır özelliklerin tümünü karşılayan belirleyin.  
  
|Bağlama|Birlikte Çalışabilirlik|(Varsayılan) güvenlik modu|Oturum<br /><br /> (Varsayılan)|İşlemler|Çift Yönlü|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Temel Profil 1.1|(Hiçbiri) taşıma, Message, karma|Yok, (yok)|(Hiçbiri)|yok|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Karma hiçbiri, taşıma (mesaj)|(Hiçbiri) taşıma, güvenilir oturum|Evet (hiçbiri)|yok|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|Karma hiçbiri, taşıma (mesaj)|(Hiçbiri) taşıma, güvenilir oturum|Evet (hiçbiri)|yok|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Hiçbiri (mesaj)|(Güvenilir oturum)|Evet (hiçbiri)|Evet|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Hiçbiri (mesaj), karma|(Hiçbiri) güvenilir oturum|Evet (hiçbiri)|Hayır|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Hiçbiri (mesaj), karma|(Hiçbiri) güvenilir oturum|Evet (hiçbiri)|Hayır|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Hiçbiri (taşıma), Message,<br /><br /> Karma|Güvenilir oturum, (taşıma)|Evet (hiçbiri)|Evet|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Yok,<br /><br /> (Taşıma)|Hiçbiri (taşıma)|Evet (hiçbiri)|Evet|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Yoktur, ileti (taşıma), her ikisi de|(Hiçbiri)|Evet (hiçbiri)|Hayır|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eş|Yoktur, ileti (taşıma), karma|(Hiçbiri)|(Hiçbiri)|Evet|  
|<xref:System.ServiceModel.WebHttpBinding>|.NET|None, taşıma, TransportCredentialOnly|(Hiçbiri)|(Hiçbiri)|yok|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Hiçbiri (taşıma)|(Hiçbiri)|Evet (hiçbiri)|yok|  
  
 Aşağıdaki tabloda, önceki tabloda bulunan özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|  
|-------------|-----------------|  
|Birlikte çalışabilirlik türü|Adları protokolü veya teknolojisi ile birlikte çalışabilirlik bağlama sağlar.|  
|Güvenlik|Kanal güvenliği nasıl belirtir:<br /><br /> -Yok: SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.<br />-Taşıma: Aktarım katmanında, güvenlik gereksinimleri karşılanır.<br />-İleti: İleti katmanında, güvenlik gereksinimleri karşılanır.<br />-Karma: Bu güvenlik modu olarak da bilinen `TransportWithMessageCredentials`. İleti düzeyi kimlik bilgilerini yönetir ve bütünlüğü ve gizlilik gereksinimleri Aktarım katmanı tarafından karşılanır.<br />-Hem: Her iki ileti düzeyi ve aktarım düzeyi güvenlik kullanılır. Bu özellik için benzersiz <xref:System.ServiceModel.NetMsmqBinding>.|  
|Oturum|Bu bağlama oturum sözleşmeleri destekleyip desteklemediğini belirtir.|  
|İşlemler|İşlem etkin olup olmadığını belirtir.|  
|Çift Yönlü|Çift yönlü sözleşmeler desteklenip desteklenmediğini belirtir. Bu özellik oturumlar için destek, bağlama gerektirir. unutmayın.|  
|Akış|İleti akış desteklenip desteklenmediğini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
