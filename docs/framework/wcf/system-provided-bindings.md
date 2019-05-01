---
title: Sistem tarafından sağlanan bağlamalar
description: Tüm sistem tarafından sağlanan Windows Communication Foundation (WCF) bağlama hakkında bilgi edinin.
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 3c6c6b628d208aede8c547dcfa66fc189a26ae01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791514"
---
# <a name="system-provided-bindings"></a>Sistem tarafından sağlanan bağlamalar

Bir uç noktaya konuşurken kullanın ve bir uç noktaya bağlanmak nasıl göstermek için iletişim mekanizması bağlantılarını belirtin. Bağlama, aşağıdaki öğeleri içerir:

- Protokol yığını, güvenlik, güvenilirlik ve uç noktasına gönderilen iletileri için kullanılacak bağlam akış ayarları belirler.

- Taşıma uç noktaya, örneğin, TCP veya HTTP iletileri gönderirken kullanılacak temel alınan Aktarım Protokolü belirler.

- Kodlama uç noktasına gönderilen iletileri için kullanılacak kodlama kablo belirler. Örneğin, metin/XML, ikili veya ileti aktarım en iyi duruma getirme mekanizması (MTOM).

 Bu makalede, tüm sistem tarafından sağlanan Windows Communication Foundation (WCF) bağlamaları sunar. Bu bağlamaları hiçbiri uygulamanızın tam ölçütlerini karşılıyorsa, özel bir bağlama oluşturabilirsiniz. Özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [özel bağlamalar](./extending/custom-bindings.md).

 WS-Federasyon protokolünü destekleyen güvenli ve birlikte çalışabilen bağlama verimli bir şekilde kimliğini doğrulamak ve kullanıcılara yetki vermek için bir Federasyon kuruluşlar sağlar.

> [!IMPORTANT]
> Her zaman güvenlik içeren bir bağlama'ı seçin. Varsayılan olarak, tüm bağlamaları dışında [ \<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) öğe olan güvenliği etkinleştirilmiş. Güvenli bir bağlama işaretlemeyin veya güvenliği devre dışı bırakmak, güvenli veri merkezinde veya yalıtılmış bir ağda depolanması gibi başka bir yolla, verilerinizi korumak emin olun.

> [!IMPORTANT]
> Güvenlik verilerinin güvenliğini sürece başka bir yolla tarafından devre dışı olan veya hiçbir zaman güvenlik desteklemeyen bağlamaları ile çift yönlü sözleşmeler'ı kullanın.

WCF ile aşağıdaki bağlamaları gönderin:

|Bağlama|Yapılandırma öğesi|Açıklama|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md)|WS-temel profil-uyumlu Web Hizmetleri ile Örneğin, ASP.NET Web hizmetlerini (ASMX) iletişim kurmak için uygun bir bağlama-tabanlı hizmetler. Bu bağlama taşıma ve metin/XML ileti kodlama varsayılan olarak HTTP kullanır.|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|Uygun olmayan yönlü Hizmet sözleşmeleri için güvenli ve birlikte çalışabilen bağlama.|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü Hizmet sözleşmeleri veya SOAP aracıları üzerinden haberleşme için uygun olan güvenli ve birlikte çalışabilen bağlama.|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Bir güvenli ve birlikte çalışabilen bağlama verimli bir şekilde kimliğini doğrulamak ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların WS-Federasyon protokolünü destekler.|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding >](../configure-apps/file-schema/wcf/nethttpbinding.md)|İkili kodlama varsayılan olarak HTTP ya da WebSocket hizmetlerini kullanma için tasarlanmış bir bağlama kullanır.|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding >](../configure-apps/file-schema/wcf/nethttpsbinding.md)|İkili kodlama varsayılan olarak HTTP ya da WebSocket hizmetlerini kullanma için tasarlanan güvenli bir bağlama kullanır.|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|Bir güvenli ve en iyi duruma getirilmiş bağlama WCF uygulamalar arasında çapraz makine haberleşmesi için uygundur.|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Makinede, WCF uygulamalar arasında iletişim için uygun olan güvenli, güvenilir ve iyileştirilmiş bir bağlama.|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../configure-apps/file-schema/wcf/netmsmqbinding.md)|Sıraya alınan bir bağlama WCF uygulamalar arasında çapraz makine haberleşmesi için uygundur.|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Birden çok makine iletişimi sağlayan bir bağlama.|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|WCF uygulaması ve uygulamaları mevcut ileti arasında çapraz makine haberleşmesi için uygun olan bir bağlama.|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding >](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|WS-temel profil uyumlu Web Hizmetleri ile iletişim kurmak için uygun bağlama, bağlam değişimi için kullanılan HTTP tanımlama bilgileri sağlar.|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Güvenli ve en iyi duruma getirilmiş WCF uygulamalar arasında çapraz makine haberleşmesi için uygun bağlama, bağlam değişimi için kullanılan SOAP üst bilgileri sağlar.|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP iletileri yerine HTTP istekleri aracılığıyla kullanıma sunulan WCF Web Hizmetleri için uç noktası yapılandırmak için kullanılan bir bağlama.|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Bağlam değişimi için kullanılan SOAP üstbilgileri sağlayan güvenli ve birlikte çalışabilen bağlama olmayan yönlü Hizmet sözleşmeleri için uygun.|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding >](../configure-apps/file-schema/wcf/udpbinding.md)|Çok sayıda basit iletileri çok sayıda istemci için aynı anda gönderilirken kullanılacak bir bağlama.|

 Aşağıdaki tabloda, her birinin sistem tarafından sağlanan bağlamalar özellikleri gösterilmektedir. Tablo sütunlarını bağlamaları bulunur; Özellikler satırlarda listelenen ve ikinci bir tabloda açıklanır. Aşağıdaki tabloda kullanılan bağlama kısaltmalar için bir anahtar sağlar. Bir bağlama seçmek için hangi sütunun ihtiyacınız satır özelliklerin tümünü karşılayan belirleyin.

|Bağlama|Birlikte Çalışabilirlik|Güvenlik (varsayılan)|Oturum<br />(Varsayılan)|İşlemler|Çift Yönlü|Kodlama (varsayılan)|Akış<br />(Varsayılan)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Temel Profil 1.1|(Hiçbiri) taşıma, Message, karma|(Hiçbiri)|(Hiçbiri)|yok|Metin (MTOM)|Evet<br />(arabelleğe alındı)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|Aktarım, karma (mesaj)|(Hiçbiri) güvenilir oturum, güvenlik oturumu|Evet (hiçbiri)|yok|(Metin) MTOM|Hayır|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Mesaj) yok|(Güvenilir oturum), güvenlik oturumu|Evet (hiçbiri)|Evet|(Metin) MTOM|Hayır|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(, Karma, None ileti)|(Hiçbiri) güvenilir oturum, güvenlik oturumu|Evet (hiçbiri)|Hayır|(Metin) MTOM|Hayır|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Hiçbiri) taşıma, Message, TransportWithMessageCredential, TransportCredentialOnly|Aşağıdaki nota bakın|None|Aşağıdaki nota bakın|(İkili), metin, MTOM|Evet (arabelleğe alındı)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Taşıma), TransportWithMessageCredential|Aşağıdaki nota bakın|Yok.|Aşağıdaki nota bakın|(İkili), metin, MTOM|Evet<br />(arabelleğe alındı)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Taşıma), Message, None, karma|(Taşıma), güvenilir oturum, güvenlik oturumu|Evet (hiçbiri)|Evet|İkili|Evet<br />(arabelleğe alındı)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Taşıma) yok|Hiçbiri (taşıma)|Evet (hiçbiri)|Evet|İkili|Evet<br />(arabelleğe alındı)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|İleti (taşıma) yok|(Hiçbiri) taşıma|Hiçbiri (Evet)|Hayır|İkili|Hayır|
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eş|(Taşıma)|(Hiçbiri)|(Hiçbiri)|Evet||Hayır|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Taşıma)|(Hiçbiri)|Hiçbiri (Evet)|yok|yok|Hayır|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Temel Profil 1.1|(Hiçbiri) taşıma, Message, karma|(Hiçbiri)|(Hiçbiri)|yok|Metin (MTOM)|Evet<br />(arabelleğe alındı)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Taşıma), Message, None, karma|(Taşıma), güvenilir oturum, güvenlik oturumu|Evet (hiçbiri)|Evet|İkili|Evet<br />(arabelleğe alındı)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Aktarım, karma (mesaj)|(Hiçbiri) güvenilir oturum, güvenlik oturumu|Evet (hiçbiri)|yok|Metin (MTOM)|Hayır|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **Not:**  Birlikte çalışabilirlik, bu bağlama uygulayan standart SOAP üzerinden UDP spec uygulayarak gerçekleştirilebilir.|.NET|(Hiçbiri)|(Hiçbiri)|(Hiçbiri)|yok|(Metin)|Hayır|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> HTTP veya WebSocket hizmetlerini kullanma için tasarlanmış bir bağlama ve ikili kodlama varsayılan olarak kullanır. <xref:System.ServiceModel.NetHttpBinding> bir istek-yanıt anlaşması veya çift yönlü sözleşme ile kullanılır ve eşleşecek şekilde davranışını değiştirir olup olmadığını algılar; HTTP istek-yanıt ve WebSockets için çift yönlü için kullanır. Bu davranış kullanılarak geçersiz kılınabilir <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ayarı bağlama: WhenDuplex - bu varsayılan değerdir ve yukarıda açıklandığı gibi davranır. Hiçbir zaman - bu WebSockets kullanılmasını engeller. Bu ayar sonuçları bir özel durum ile çift yönlü sözleşme kullanılmaya çalışılıyor. Her zaman - bile istek-yanıt sözleşmeleriyle için kullanılacak WebSockets zorlar. NetHttpBinding güvenilir oturumlar hem HTTP modu hem de WebSocket modu destekler. WebSocket içinde modu oturumları taşıma tarafından sağlanır.

 Aşağıdaki tabloda, yukarıdaki tabloda listelenen özellikleri açıklanmaktadır.

|Özellik|Açıklama|
|-------------|-----------------|
|Birlikte çalışabilirlik türü|Adları protokolü veya teknolojisi ile birlikte çalışabilirlik bağlama sağlar.|
|Güvenlik|Kanal güvenliği nasıl belirtir:<br />-Yok: SOAP iletisi güvenli değilse ve istemci kimliği değil.<br />-Taşıma: Aktarım katmanında, güvenlik gereksinimleri karşılanır.<br />-İleti: İleti katmanında, güvenlik gereksinimleri karşılanır.<br />-Karma: Talep iletisinde taşınır; bütünlüğü ve gizlilik gereksinimleri, Aktarım katmanı tarafından karşılanır.|
|Oturum|Bu bağlama oturum sözleşmeleri destekleyip desteklemediğini belirtir.|
|İşlemler|İşlem etkin olup olmadığını belirtir.|
|Çift Yönlü|Çift yönlü sözleşmeler desteklenip desteklenmediğini belirtir. Bu özellik oturumlar için destek bağlamasında gerektiğini unutmayın.|
|Encoding|İleti gönderme biçimini belirtir. İzin verilen değerler şunlardır:<br />-Metin: Örneğin UTF-8.<br />-İkili<br />-İleti Aktarım en iyi duruma getirme mekanizması (MTOM): SOAP Zarfı bağlamında ikili XML öğeleri verimli bir şekilde kodlama yöntemi.|
|Akış|Akış gelen ve giden iletiler için desteklenip desteklenmediğini belirtir. Kullanım `TransferMode` değeri ayarlamak için bağlama özelliği. İzin verilen değerler şunlardır:<br />- <xref:System.ServiceModel.TransferMode.Buffered>: İstek ve yanıt iletilerinin hem arabelleğe alınır.<br />- <xref:System.ServiceModel.TransferMode.Streamed>: İstek ve yanıt iletilerinin hem de aktarılır.<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: İstek iletisi sağlanacağına ve yanıt iletisi arabelleğe alındı.<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: İstek iletisi arabelleğe alınır ve yanıt iletisi akış.|

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Oluşturmaya Genel Bakış](endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
- [Temel WCF Programlama](basic-wcf-programming.md)
