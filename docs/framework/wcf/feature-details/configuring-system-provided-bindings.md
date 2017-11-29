---
title: "Sistem Tarafından Sağlanan Bağlamaları Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c26a4f804f99fda637937bfa5ddaef218c15ede7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamaları Yapılandırma
Bağlamalar ve bir bitiş noktasına bağlanmak nasıl belirtmek için bir uç nokta konuşurken kullanmak için iletişim mekanizması belirtin. Bağlamaları oluşur tanımlayan öğeleri nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanalları katmanlı yedeklemek için gerekli iletişim özelliklerini sağlamak için. Bağlama öğeleri üç tür içerir:  
  
-   Güvenlik, güvenilirlik, içeriği akış ayarları veya kullanıcı tanımlı protokolleri uç noktasına gönderilen iletileri ile birlikte kullanmak için belirleyen Protokolü kanal bağlama öğeleri.  
  
-   Uç nokta için örneğin, TCP veya HTTP iletileri gönderirken kullanmak için temel Aktarım Protokolü belirlemek kanal bağlama öğelerini taşıma.  
  
-   Kablo text/XML, ikili, örneğin, uç noktasına gönderilen iletiler için kullanılacak kodlamayı bağlama öğeleri kodlama ileti veya ileti iletim en iyi duruma getirme mekanizmasını (MTOM).  
  
 Bu konuda tüm sistem tarafından sağlanan sunulmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bağlar. Hiçbiri, uygulamanız için tam gereksinimleri karşılıyorsa, kullanarak bir bağlama oluşturabilirsiniz <xref:System.ServiceModel.Channels.CustomBinding> sınıfı. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel bağlama oluşturma, bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Güvenliği etkinleştirilmiş sahip bir bağlama seçin. Varsayılan olarak, tüm bağlamaları dışında <xref:System.ServiceModel.BasicHttpBinding> bağlama, güvenliği etkinleştirilmiş olması. Güvenli bağlama seçmezseniz veya güvenlik devre dışı bırakırsanız, ağ iletişimlerini güvenli veri merkezinde veya yalıtılmış bir ağda olması gibi bazı diğer şekilde, korunan emin olun.  
  
> [!IMPORTANT]
>  Çift yönlü sözleşmeler güvenlik desteklemez veya başka bir şekilde ağ exchange güvenli sürece devre dışı, güvenlik sahip bağlamalarla kullanmayın.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Aşağıdaki bağlamaları ile birlikte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Bağlama|Yapılandırma öğesi|Açıklama|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|WS-temel profil uyumluluğunu Web Hizmetleri ile Örneğin, ASP.NET Web Hizmetleri (ASMX) iletişim kurmak için uygun olan bir bağlama-services tabanlı. Bu bağlama taşıma ve varsayılan ileti kodlama olarak text/XML olarak HTTP kullanır.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Olmayan yönlü Hizmet sözleşmeleri için uygun bir güvenli ve birlikte çalışabilir bağlama.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Doğru sürümleri için destek sağlayan bir güvenli ve birlikte çalışabilir bağlama <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğeleri.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli ve birlikte çalışabilir bağlama.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Güvenli ve birlikte çalışabilir, bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların etkinleştirme WS-Federasyon protokolünü destekler.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Türetilen bir güvenli ve birlikte çalışabilir bağlama <xref:System.ServiceModel.WS2007HttpBinding> ve Federasyon güvenlik destekler.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Güvenli ve en iyi duruma getirilmiş bağlama arasında makineler arası iletişim için uygun [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Makine üzerindeki arasındaki iletişim için uygun bir güvenli, güvenilir ve en iyi duruma getirilmiş bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Arasında makineler arası iletişim için uygun bir sıralı bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Güvenli, çok makineli iletişimi sağlayan bir bağlama.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Uç noktaları için yapılandırmak için kullanılan bir bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri SOAP iletilerine yerine HTTP istekleri aracılığıyla sunulur.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<MsmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Bir bağlama arasında makineler arası iletişim için uygun olan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ve uygulamalara Message Queuing (MSMQ olarak da bilinir).|  
  
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
 [Uç noktası oluşturma genel bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
