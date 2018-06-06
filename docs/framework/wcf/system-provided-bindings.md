---
title: Sistem tarafından sağlanan bağlamalar
description: Tüm sistem tarafından sağlanan Windows Communication Foundation (WCF) bağlamalar hakkında bilgi edinin.
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 6730238a73b41faa4409fdfc75af1de36f31d13e
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805652"
---
# <a name="system-provided-bindings"></a>Sistem tarafından sağlanan bağlamalar

Bağlamalar ve bir bitiş noktasına bağlanmak nasıl belirtmek için bir uç nokta konuşurken kullanmak için iletişim mekanizması belirtin. Bir bağlama aşağıdaki öğeleri içerir:

- Protokol yığını güvenlik, güvenilirlik ve uç noktasına gönderilen iletileri için kullanılacak bağlam akış ayarları belirler.

- Taşıma uç noktasına, örneğin, TCP veya HTTP iletileri gönderirken kullanmak için temel Aktarım Protokolü belirler.

- Kodlama uç noktasına gönderilen iletileri için kullanılacak kodlama kablo belirler. Örneğin, text/XML, ikili veya ileti iletim en iyi duruma getirme mekanizmasını (MTOM).

 Bu makalede, tüm sistem tarafından sağlanan Windows Communication Foundation (WCF) bağlamalar gösterir. Bu bağlamaların hiçbiri uygulamanız için tam ölçütleri karşılamıyorsa, özel bir bağlama oluşturabilirsiniz. Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [özel bağlamalar](./extending/custom-bindings.md).

 WS-Federasyon protokolünü destekleyen bir güvenli ve birlikte çalışabilir bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon kuruluşlar sağlar.

> [!IMPORTANT]
> Her zaman güvenlik içeren bir bağlama seçin. Varsayılan olarak, tüm bağlamaları dışında [ \<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesi güvenliği etkinleştirilmiş olması. Güvenli bağlama işaretlemeyin veya güvenlik devre dışı bırakmak, güvenli veri merkezinde veya yalıtılmış bir ağda depolamak gibi bazı diğer şekilde, verilerinizi korumak emin olun.

> [!IMPORTANT]
> Verilerin güvenliği sürece başka bir şekilde devre dışı güvenlik sahip veya hiçbir zaman çift yönlü sözleşmeler güvenlik desteklemeyen bağlamalarla kullanın.

WCF ile aşağıdaki bağlamaları sevk:

|Bağlama|Yapılandırma öğesi|Açıklama|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md)|WS-temel profil-uyumluluğunu Web Hizmetleri ile Örneğin, ASP.NET Web Hizmetleri (ASMX) iletişim kurmak için uygun olan bir bağlama-services tabanlı. Bu bağlama taşıma ve varsayılan ileti kodlama olarak text/XML olarak HTTP kullanır.|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|Olmayan yönlü Hizmet sözleşmeleri için uygun bir güvenli ve birlikte çalışabilir bağlama.|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli ve birlikte çalışabilir bağlama.|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Güvenli ve birlikte çalışabilir, bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların WS-Federasyon protokolünü destekler.|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding >](../configure-apps/file-schema/wcf/nethttpbinding.md)|HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış bir bağlama ikili kodlama varsayılan olarak kullanılır.|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding >](../configure-apps/file-schema/wcf/nethttpsbinding.md)|HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış güvenli bağlama ikili kodlama varsayılan olarak kullanılır.|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|Güvenli ve en iyi duruma getirilmiş bağlama WCF uygulamalar arasında makineler arası iletişim için uygundur.|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Makine üzerindeki WCF uygulamaları arasındaki iletişim için uygun bir güvenli, güvenilir ve en iyi duruma getirilmiş bağlama.|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../configure-apps/file-schema/wcf/netmsmqbinding.md)|Sıraya alınan bir bağlama WCF uygulamalar arasında makineler arası iletişim için uygundur.|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Birden fazla makine iletişimi sağlayan bir bağlama.|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|WCF uygulaması ve var olan Message Queuing uygulamalar arasında makineler arası iletişim için uygun bir bağlama.|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding >](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|WS-temel profil uyumluluğunu Web Hizmetleri ile iletişim kurmak için uygun bir bağlama, bağlam değişimi için kullanılacak HTTP tanımlama bilgilerini sağlar.|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Güvenli ve en iyi duruma getirilmiş WCF uygulamaları arasındaki makineler arası iletişim için uygun bağlama, bağlam değişimi için kullanılacak SOAP üstbilgileri sağlar.|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP iletilerine yerine HTTP istekleri aracılığıyla kullanıma sunulan WCF Web hizmeti için uç noktalar yapılandırmak için kullanılan bir bağlama.|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Bağlam değişimi için kullanılacak SOAP üstbilgileri sağlayan bir güvenli ve birlikte çalışabilir bağlama olmayan yönlü Hizmet sözleşmeleri için uygun.|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding >](../configure-apps/file-schema/wcf/udpbinding.md)|Çok sayıda basit iletileri çok sayıda istemci için aynı anda gönderirken kullanmak için bir bağlama.|

 Aşağıdaki tabloda her bir sistem tarafından sağlanan bağlamalar özellikleri gösterilmektedir. Bağlamaları tablo sütunları bulunur; Özellikler satırları listelenen ve ikinci bir tabloda açıklanmaktadır. Aşağıdaki tabloda kullanılan bağlama kısaltmalar için bir anahtar sağlar. Bir bağlama seçmek için gereksinim duyduğunuz satır özelliklerin tümü, hangi sütunun karşılayan belirler.

|Bağlama|Birlikte Çalışabilirlik|Güvenlik (varsayılan)|Oturum<br />(Varsayılan)|İşlemler|Çift Yönlü|Kodlama (varsayılan)|Akış<br />(Varsayılan)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Temel Profil 1.1|(Hiçbiri), Aktarım, ileti, karma|(Hiçbiri)|(Hiçbiri)|yok|Metin, (MTOM)|Evet<br />(arabelleğe)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|Taşıma, karma (ileti)|(Hiçbiri), güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|yok|(Metin) MTOM|Hayır|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(İleti) yok|(Güvenilir oturum), güvenlik oturumu|(Hiçbiri), Evet|Evet|(Metin) MTOM|Hayır|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federasyon|(, Karma, hiçbiri ileti)|(Hiçbiri), güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|Hayır|(Metin) MTOM|Hayır|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Hiçbiri), Aktarım, ileti, TransportWithMessageCredential, TransportCredentialOnly|Aşağıdaki nota bakın|Yok.|Aşağıdaki nota bakın|(İkili), metin, MTOM|Evet (arabelleğe)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Aktarım) TransportWithMessageCredential|Aşağıdaki nota bakın|Yok.|Aşağıdaki nota bakın|(İkili), metin, MTOM|Evet<br />(arabelleğe)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Aktarım) None, ileti karma|(Aktarım) güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|Evet|İkili|Evet<br />(arabelleğe)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Aktarım) yok|Hiçbiri (aktarım)|(Hiçbiri), Evet|Evet|İkili|Evet<br />(arabelleğe)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|İleti, (aktarım) yok|(Hiçbiri), Aktarım|Hiçbiri (Evet)|Hayır|İkili|Hayır|
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eş|(Aktarım)|(Hiçbiri)|(Hiçbiri)|Evet||Hayır|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Aktarım)|(Hiçbiri)|Hiçbiri (Evet)|yok|yok|Hayır|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Temel Profil 1.1|(Hiçbiri), Aktarım, ileti, karma|(Hiçbiri)|(Hiçbiri)|yok|Metin, (MTOM)|Evet<br />(arabelleğe)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Aktarım) None, ileti karma|(Aktarım) güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|Evet|İkili|Evet<br />(arabelleğe)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Taşıma, karma (ileti)|(Hiçbiri), güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|yok|Metin, (MTOM)|Hayır|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **Not:** birlikte çalışabilirlik elde edilebilir bu bağlamayı gerçekleştiren standart SOAP üzerinden UDP spec uygulayarak.|.NET|(Hiçbiri)|(Hiçbiri)|(Hiçbiri)|yok|(Metin)|Hayır|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış bir bağlama ve ikili kodlama varsayılan olarak kullanır. <xref:System.ServiceModel.NetHttpBinding> İstek-yanıt sözleşmesi ya da çift yönlü sözleşme ile kullanılır ve eşleşecek şekilde davranışını değiştirir olup olmadığını algılar; HTTP istek-yanıt ve WebSockets için çift yönlü için kullanır. Bu davranış kullanılarak geçersiz kılınabilir <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ayarı bağlama: WhenDuplex - bu varsayılan değerdir ve yukarıda açıklandığı gibi davranır. Hiçbir zaman - bu WebSockets kullanılmasını engeller. Bu ayar sonuçları bir özel durum ile çift yönlü sözleşme kullanılmaya çalışılıyor. Her zaman - bu bile istek-yanıt sözleşmeleri için kullanılacak WebSockets zorlar. NetHttpBinding güvenilir oturumlar hem HTTP modu hem de WebSocket modu destekler. WebSocket içinde modu oturumları taşıma tarafından sağlanır.

 Aşağıdaki tabloda önceki tabloda listelenen özellikleri açıklanmaktadır.

|Özellik|Açıklama|
|-------------|-----------------|
|Birlikte çalışabilirlik türü|Adları protokolü veya teknolojisi ile birlikte çalışma bağlama sağlar.|
|Güvenlik|Kanal güvenliği nasıl belirtir:<br />-Hiçbiri: SOAP iletisi güvenli değildir ve istemci kimliği değil.<br />-Taşıma: Güvenlik gereksinimlerini aktarım katmanında karşılanır.<br />-İleti: Güvenlik gereksinimlerini ileti katmanında karşılanır.<br />-Karma: Talep iletide taşınır; bütünlüğü ve gizliliği gereksinimleri Aktarım katmanı tarafından karşılanır.|
|Oturum|Bu bağlama oturum sözleşmeleri destekleyip desteklemediğini belirtir.|
|İşlemler|İşlemler etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|Çift Yönlü|Çift yönlü sözleşmeler desteklenip desteklenmediğini belirtir. Bu özellik oturumları için destek bağlamasında gerektirdiğini unutmayın.|
|Kodlama|İleti gönderme biçimini belirtir. İzin verilen değerler şunlardır:<br />-Metin: Örneğin UTF-8.<br />-İkili<br />-İleti iletim en iyi duruma getirme mekanizmasını (MTOM): ikili XML öğeleri bir SOAP Zarfı bağlamında verimli bir şekilde kodlama için bir yöntem.|
|Akış|Akış gelen ve giden iletiler için desteklenip desteklenmediğini belirtir. Kullanım `TransferMode` değerini ayarlamak için bağlama özelliği. İzin verilen değerler şunlardır:<br />- <xref:System.ServiceModel.TransferMode.Buffered>: İstek ve yanıt iletileri hem arabelleğe alınmış.<br />- <xref:System.ServiceModel.TransferMode.Streamed>: İstek ve yanıt iletileri hem akışa alınır.<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: İstek iletisi akışı ve yanıt iletisi arabelleğe alındı.<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: İstek iletisi arabelleğe ve yanıt iletisi akışı.|

## <a name="see-also"></a>Ayrıca bkz.

[Uç Nokta Oluşturmaya Genel Bakış](endpoint-creation-overview.md)  
[Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)  
[Temel WCF Programlama](basic-wcf-programming.md)  
