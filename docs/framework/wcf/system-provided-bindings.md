---
title: "Sistem Tarafından Sağlanan Bağlamalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5f8df31e31c9617fe7bcd92789671d220382a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar
Bağlamalar ve bir bitiş noktasına bağlanmak nasıl belirtmek için bir uç nokta konuşurken kullanmak için iletişim mekanizması belirtin. Bir bağlama aşağıdaki öğeleri içerir:  
  
-   Protokol yığını güvenlik, güvenilirlik ve uç noktasına gönderilen iletileri için kullanılacak bağlam akış ayarları belirler.  
  
-   Taşıma uç noktasına, örneğin, TCP veya HTTP iletileri gönderirken kullanmak için temel Aktarım Protokolü belirler.  
  
-   Kodlama uç noktasına örneğin gönderilen iletiler, text/XML, ikili veya ileti iletim en iyi duruma getirme mekanizmasını (MTOM) için kullanılacak kodlama kablo belirler.  
  
 Bu konuda tüm sistem tarafından sağlanan sunulmaktadır [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] bağlar. Hiçbiri uygulamanızın tam ölçütlerini karşılıyorsa, özel bir bağlama oluşturabilirsiniz. [!INCLUDE[crabout](../../../includes/crabout-md.md)]özel bağlama oluşturma, bkz: [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 WS-Federasyon protokolünü destekleyen bir güvenli ve birlikte çalışabilir bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon kuruluşlar sağlar.  
  
> [!IMPORTANT]
>  Her zaman güvenlik içeren bir bağlama seçin. Varsayılan olarak, tüm bağlamaları dışında [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi güvenliği etkinleştirilmiş olması. Güvenli bağlama işaretlemeyin veya güvenlik devre dışı bırakmak, güvenli veri merkezinde veya yalıtılmış bir ağda depolamak gibi bazı diğer şekilde, verilerinizi korumak emin olun.  
  
> [!IMPORTANT]
>  Verilerin güvenliği sürece başka bir şekilde devre dışı güvenlik sahip veya hiçbir zaman çift yönlü sözleşmeler güvenlik desteklemeyen bağlamalarla kullanın.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Aşağıdaki bağlamaları ile birlikte gelen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
|Bağlama|Yapılandırma öğesi|Açıklama|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|WS-temel profil uyumluluğunu Web Hizmetleri ile Örneğin, ASP.NET Web Hizmetleri (ASMX) iletişim kurmak için uygun olan bir bağlama-services tabanlı. Bu bağlama taşıma ve varsayılan ileti kodlama olarak text/XML olarak HTTP kullanır.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Olmayan yönlü Hizmet sözleşmeleri için uygun bir güvenli ve birlikte çalışabilir bağlama.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli ve birlikte çalışabilir bağlama.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Güvenli ve birlikte çalışabilir, bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların WS-Federasyon protokolünü destekler.|  
|<xref:System.ServiceModel.NetHttpBinding>|\<netHttpBinding >|HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış bir bağlama ikili kodlama varsayılan olarak kullanılır.|  
|<xref:System.ServiceModel.NetHttpsBinding>|\<netHttpsBinding >|HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış güvenli bağlama ikili kodlama varsayılan olarak kullanılır.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Güvenli ve en iyi duruma getirilmiş bağlama arasında makineler arası iletişim için uygun [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Makine üzerindeki arasındaki iletişim için uygun bir güvenli, güvenilir ve en iyi duruma getirilmiş bağlama [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Arasında makineler arası iletişim için uygun bir sıralı bağlama [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Birden fazla makine iletişimi sağlayan bir bağlama.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Bir bağlama arasında makineler arası iletişim için uygun olan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulama ve var olan Message Queuing uygulamaları.|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Bağlam değişimi için kullanılacak HTTP tanımlama bilgilerini sağlayan Web Hizmetleri WS-temel profil uyumluluğunu ile iletişim kurmak için uygun bir bağlama.|  
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Güvenli ve en iyi duruma getirilmiş bağlama arasında makineler arası iletişim için uygun [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bağlam değişimi için kullanılacak SOAP üstbilgileri sağlayan uygulamalar.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Uç noktaları için yapılandırmak için kullanılan bir bağlama [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web Hizmetleri SOAP iletilerine yerine HTTP istekleri aracılığıyla sunulur.|  
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Güvenli ve |<xref:System.ServiceModel.UdpBinding>|\<udpBinding >|Çok sayıda basit iletileri çok sayıda istemci için aynı anda gönderirken kullanmak için bir bağlama.|  
  
 Aşağıdaki tabloda her bir sistem tarafından sağlanan bağlamalar özellikleri gösterilmektedir. Bağlamaları tablo sütunları bulunur; Özellikler satırları listelenen ve ikinci bir tabloda açıklanmaktadır. Aşağıdaki tabloda kullanılan bağlama kısaltmalar için bir anahtar sağlar. Bir bağlama seçmek için gereksinim duyduğunuz satır özelliklerin tümü, hangi sütunun karşılayan belirler.  
  
|Bağlama|Birlikte Çalışabilirlik|Güvenlik (varsayılan)|Oturum<br /><br /> (Varsayılan)|İşlemler|Çift Yönlü|Kodlama (varsayılan)|Akış<br /><br /> (Varsayılan)|  
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Temel Profil 1.1|(Hiçbiri), Aktarım, ileti, karma|(Hiçbiri)|(Hiçbiri)|yok|Metin, (MTOM)|Evet<br /><br /> (arabelleğe)|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Taşıma, karma (ileti)|(Hiçbiri), güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|yok|(Metin) MTOM|Hayır|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(İleti) yok|(Güvenilir oturum), güvenlik oturumu|(Hiçbiri), Evet|Evet|(Metin) MTOM|Hayır|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federasyon|(, Karma, hiçbiri ileti)|(Hiçbiri), güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|Hayır|(Metin) MTOM|Hayır|  
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Hiçbiri), Aktarım, ileti, TransportWithMessageCredential, TransportCredentialOnly|Aşağıdaki nota bakın|Yok.|Aşağıdaki nota bakın|(İkili), metin, MTOM|Evet (arabelleğe)|  
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Aktarım) TransportWithMessageCredential|Aşağıdaki nota bakın|Yok.|Aşağıdaki nota bakın|(İkili), metin, MTOM|Evet (arabelleğe)|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Aktarım) None, ileti karma|(Aktarım) güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|Evet|İkili|Evet<br /><br /> (arabelleğe)|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Aktarım) yok|Hiçbiri (aktarım)|(Hiçbiri), Evet|Evet|İkili|Evet<br /><br /> (arabelleğe)|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|İleti, (aktarım) yok|(Hiçbiri), Aktarım|Hiçbiri (Evet)|Hayır|İkili|Hayır|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Eş|(Aktarım)|(Hiçbiri)|(Hiçbiri)|Evet||Hayır|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Aktarım)|(Hiçbiri)|Hiçbiri (Evet)|yok|yok|Hayır|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|Temel Profil 1.1|(Hiçbiri), Aktarım, ileti, karma|(Hiçbiri)|(Hiçbiri)|yok|Metin, (MTOM)|Evet<br /><br /> (arabelleğe)|  
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Aktarım) None, ileti karma|(Aktarım) güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|Evet|İkili|Evet<br /><br /> (arabelleğe)|  
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Taşıma, karma (ileti)|(Hiçbiri), güvenilir oturum, güvenlik oturumu|(Hiçbiri), Evet|yok|Metin, (MTOM)|Hayır|  
|<xref:System.ServiceModel.UdpBinding>|.NET **Not:** birlikte çalışabilirlik elde edilebilir bu bağlamayı gerçekleştiren standart SOAP üzerinden UDP spec uygulayarak.|(Hiçbiri)|(Hiçbiri)|(Hiçbiri)|yok|(Metin)|Hayır|  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.NetHttpBinding>HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış bir bağlama ve ikili kodlama varsayılan olarak kullanır. <xref:System.ServiceModel.NetHttpBinding>İstek-yanıt sözleşmesi ya da çift yönlü sözleşme ile kullanılan olup olmadığını algılar ve eşleşecek şekilde davranışını değiştirme - Bunu HTTP istek-yanıt ve WebSockets için çift yönlü için kullanır. Bu davranış kullanılarak geçersiz kılınabilir <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A>--> `System.ServiceModel.NetHttpBinding.WebSocketTransportUsage` ayarı bağlama: izin verilen - bu varsayılan değerdir ve yukarıda açıklandığı gibi davranır. QueuedDeliveryRequirements - bu WebSockets kullanılmasını engeller. Çift yönlü sözleşme ile bu ayarı kullanın çalışılırken bir özel durum neden olur. Gerekli - bu bile istek-yanıt sözleşmeleri için kullanılacak WebSockets zorlar. NetHttpBinding güvenilir oturumlar hem HTTP modu hem de WebSocket modu destekler. WebSocket içinde modu oturumları taşıma tarafından sağlanır.  
  
 Aşağıdaki tabloda önceki tabloda listelenen özellikleri açıklanmaktadır.  
  
|Özellik|Açıklama|  
|-------------|-----------------|  
|Birlikte çalışabilirlik türü|Adları protokolü veya teknolojisi ile birlikte çalışma bağlama sağlar.|  
|Güvenlik|Kanal güvenliği nasıl belirtir:<br /><br /> -Hiçbiri: SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.<br />-Taşıma: Güvenlik gereksinimlerini aktarım katmanında karşılanır.<br />-İleti: Güvenlik gereksinimlerini ileti katmanında karşılanır.<br />-Karma: Talep iletide taşınır; bütünlüğü ve gizliliği gereksinimleri Aktarım katmanı tarafından karşılanır.|  
|Oturum|Bu bağlama oturum sözleşmeleri destekleyip desteklemediğini belirtir.|  
|İşlemler|İşlemler etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|Çift Yönlü|Çift yönlü sözleşmeler desteklenip desteklenmediğini belirtir. Bu özellik oturumları için destek bağlamasında gerektirdiğini unutmayın.|  
|Kodlama|İleti gönderme biçimini belirtir. İzin verilen değerler şunlardır:<br /><br /> -Metin: Örneğin UTF-8.<br />-İkili<br />-İleti iletim en iyi duruma getirme mekanizmasını (MTOM): ikili XML öğeleri bir SOAP Zarfı bağlamında verimli bir şekilde kodlama için bir yöntem.|  
|Akış|Akış gelen ve giden iletiler için desteklenip desteklenmediğini belirtir. Kullanım `TransferMode` değerini ayarlamak için bağlama özelliği. İzin verilen değerler şunlardır:<br /><br /> -   <xref:System.ServiceModel.TransferMode.Buffered>: İstek ve yanıt iletileri hem arabelleğe alınmış.<br />-   <xref:System.ServiceModel.TransferMode.Streamed>: İstek ve yanıt iletileri hem akışa alınır.<br />-   <xref:System.ServiceModel.TransferMode.StreamedRequest>: İstek iletisi akışı ve yanıt iletisi arabelleğe alındı.<br />-   <xref:System.ServiceModel.TransferMode.StreamedResponse>: İstek iletisi arabelleğe ve yanıt iletisi akışı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)
