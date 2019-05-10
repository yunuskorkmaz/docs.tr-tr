---
title: Bağlamalar ve Güvenlik
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 12296fbd503a7e9f1866f407964a5e223d1afadd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650326"
---
# <a name="bindings-and-security"></a>Bağlamalar ve Güvenlik
Windows Communication Foundation (WCF) dahil sistem tarafından sağlanan bağlamalar program WCF uygulamaları için hızlı bir yol sunar. Bunun tek istisnası, etkin bir varsayılan güvenlik düzeni tüm bağlamaları vardır. Bu konuda güvenlik ihtiyaçları için doğru bağlama seçmenize yardımcı olur.  
  
 WCF güvenlik genel bakış için bkz. [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). WCF bağlamaları kullanarak programlama hakkında daha fazla bilgi için bkz. [WCF güvenliğini programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Zaten bir bağlama'ı seçtiyseniz, güvenlik ile ilişkili olan çalışma zamanı davranışları hakkında daha fazla bilgi bulabilirsiniz [güvenlik davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Bazı güvenlik işlevleri, sistem tarafından sağlanan bağlamalar kullanılarak programlanabilir değildir. Özel bağlama kullanma daha fazla denetim için bkz: [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Güvenlik işlevleri bağlamaları  
 WCF çoğu gereksinimlerini sistem tarafından sağlanan bağlamalar içerir. Belirli bir bağlama yeterli değil ise, özel bir bağlama oluşturabilirsiniz. Sistem tarafından sağlanan bağlamalar bir listesi için bkz. [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md). Özel bağlamalar hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Wcf'de her bağlamanın iki biçimi vardır: bir API ve yapılandırma dosyasında kullanılan bir XML öğesi olarak. Örneğin, `WSHttpBinding` (API) içinde bir karşılığı vardır [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Aşağıdaki bölümde her bağlama için her iki biçimi listeler ve güvenlik özellikleri özetlenmektedir.  
  
### <a name="basichttp"></a>BasicHttp  
 Kod içinde kullanma <xref:System.ServiceModel.BasicHttpBinding> sınıfı; yapılandırmasında kullanmasına [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Bu bağlama, bir dizi aşağıdaki gibi mevcut teknolojiler ile kullanılmak üzere tasarlanmıştır:  
  
- ASP.NET Web Hizmetleri (ASMX), sürüm 1.  
  
- Web hizmeti geliştirmeleri (WSE) uygulamaları.  
  
- Web hizmetlerini birlikte çalışabilirlik tanımlandığı gibi temel profilini (WS-ı) belirtimi (<https://go.microsoft.com/fwlink/?LinkId=38955>).  
  
- WS içinde tanımlandığı gibi temel güvenlik profili-ediyorum.  
  
 Varsayılan olarak, bu bağlantı güvenli değil. ASMX hizmetleriyle çalışmak için tasarlanmıştır. Güvenlik etkinleştirildiğinde, Windows tümleşik güvenliği temel kimlik doğrulaması ve Özet gibi Internet Information Services (IIS) güvenlik mekanizmaları ile bağlama sorunsuz birlikte çalışma için tasarlanmıştır. Daha fazla bilgi için [aktarım güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Bu bağlama, aşağıdakileri destekler:  
  
- Aktarım güvenliği HTTPS.  
  
- HTTP temel kimlik doğrulaması.  
  
- WS-güvenlik.  
  
 Daha fazla bilgi için <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, ve <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.WSHttpBinding> sınıfı; yapılandırmasında kullanmasına [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Varsayılan olarak, bu bağlama WS-Security belirtimi uygular ve WS - uygulama hizmetleri ile birlikte çalışabilirlik sağlar * belirtimleri. Aşağıdakileri destekler:  
  
- Aktarım güvenliği HTTPS.  
  
- WS-güvenlik.  
  
- HTTPS ile SOAP ileti kimlik bilgisi güvenlik arayan kimliğini doğrulamak için koruma taşıma.  
  
 Daha fazla bilgi için <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, ve <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.WSDualHttpBinding> sınıfı; yapılandırmasında kullanmasına [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Bu bağlama, çift yönlü hizmet uygulamaları sağlamak için tasarlanmıştır. Bu bağlama, ileti tabanlı aktarım güvenliği için WS-Security belirtimi uygular. Aktarım güvenliği kullanılamıyor. Varsayılan olarak, aşağıdaki özellikleri sağlar:  
  
- WS-Reliable Mesajlaşma için güvenilirlik uygular.  
  
- Aktarım güvenliği ve kimlik doğrulaması için WS-güvenlik uygular.  
  
- HTTP ileti teslimi için kullanır.  
  
- İleti metni/XML kodlaması kullanır.  
  
 WS-güvenlik (ileti Katmanı Güvenliği) kullanarak, bağlama aşağıdaki parametreleri yapılandırmanıza olanak sağlar:  
  
- Şifreleme algoritması belirlemek için Güvenlik algoritması paketi.  
  
- Aşağıdaki seçenekler bağlama:  
  
    - Hizmet kimlik bilgileri kullanılabilir-bant istemcide sağlama.  
  
    - Kanal kurulumunun parçası olarak hizmetinden hizmet kimlik bilgilerini sağlayan anlaşma.  
  
 Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSDualHttpSecurity> ve <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.NetTcpBinding> sınıfı; yapılandırmasında kullanmasına [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Bu bağlama, çapraz makine haberleşmesi için optimize edilmiştir. Varsayılan olarak, aşağıdaki özelliklere sahiptir:  
  
- Aktarım Katmanı Güvenliği uygular.  
  
- Aktarım güvenliği ve kimlik doğrulaması için Windows Güvenlik yararlanır.  
  
- TCP aktarımı için kullanır.  
  
- Implements ikili ileti kodlama.  
  
- Uygular, WS-Reliable Mesajlaşma.  
  
 Seçenekler aşağıdakileri içerir:  
  
- İleti düzeyi güvenlik (WS-güvenlik kullanarak).  
  
- Aktarım güvenliği ileti kimlik bilgileri ile — gizliliği ve bütünlüğü WS-Security tarafından sağlanan yetkilendirme için TCP ve kimlik bilgileri Aktarım Katmanı Güvenliği (TLS) tarafından sağlanan.  
  
 Daha fazla bilgi için <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, ve <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 Kod içinde kullanma <xref:System.ServiceModel.NetNamedPipeBinding> sınıfı; yapılandırmasında kullanmasına [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Bu bağlama (genellikle aynı makinede) çapraz proses haberleşmesi için optimize edilmiştir. Varsayılan olarak, bu bağlama, aşağıdaki özelliklere sahiptir:  
  
- İleti aktarma ve kimlik doğrulaması için güvenlik kullanan taşıma.  
  
- İleti teslimi için adlandırılmış kanallar kullanır.  
  
- Implements ikili ileti kodlama.  
  
- Şifreleme ve ileti imzalama.  
  
 Seçenekler aşağıdakileri içerir:  
  
- Windows güvenliğini kullanarak kimlik doğrulaması.  
  
 Daha fazla bilgi için <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, ve <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 Kod içinde kullanma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfı; yapılandırmasında kullanmasına [ \<MsmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Bu bağlama, WCF Microsoft Message Queuing MSMQ olmayan uç noktaları ile WCF istemciler ve çalışan hizmetler oluşturmak için en iyi duruma getirilmiştir.  
  
 Varsayılan olarak, bu bağlama aktarım güvenliği kullanır ve güvenlik özellikleri sağlar:  
  
- Güvenlik olabilir (hiçbiri) devre dışı.  
  
- MSMQ taşıma güvenliği (taşıma).  
  
 Daha fazla bilgi için bkz. <xref:System.ServiceModel.NetMsmqSecurity> ve <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 Kod içinde kullanma <xref:System.ServiceModel.NetMsmqBinding> sınıfı; yapılandırmasında kullanmasına [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 MSMQ gerektiren WCF hizmetleri oluşturma kuyruğa ileti destek olduğunda bu bağlama için kullanılması amaçlanmıştır.  
  
 Varsayılan olarak, bu bağlama aktarım güvenliği kullanır ve güvenlik özellikleri sağlar:  
  
- Güvenlik olabilir (hiçbiri) devre dışı.  
  
- MSMQ taşıma güvenliği (taşıma).  
  
- SOAP tabanlı ileti güvenliği (mesaj).  
  
- Eş zamanlı aktarım iletisi güvenlik ve (her ikisi de).  
  
- İstemci kimlik bilgisi türleri desteklenir: None, Windows, kullanıcı adı, sertifika, IssuedToken.  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> Kimlik bilgisi yalnızca güvenlik modu olarak ayarlandığında desteklenir <xref:System.ServiceModel.NetMsmqSecurityMode.Both> veya <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 Daha fazla bilgi için bkz. <xref:System.ServiceModel.MessageSecurityOverMsmq> ve <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı; yapılandırmasında kullanmasına [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Varsayılan olarak, bu bağlama, WS-güvenlik (ileti Katmanı Güvenliği) kullanır.  
  
 Daha fazla bilgi için [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, ve <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Sistem tarafından sağlanan bağlamalar hiçbiri, gereksinimlerini karşılıyorsa, özel güvenlik bağlama öğesi ile özel bir bağlama oluşturabilirsiniz. Daha fazla bilgi için [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Bağlama Seçenekleri  
 Güvenlik modu ayarı sunulan özellikler aşağıdaki tabloda özetlenmiştir, diğer bir deyişle, güvenlik modu ayarlandığında özelliklerin listeler `Transport`, `Message`, veya `TransportWithMessageCredential`. Uygulamanızın gerektirdiği güvenlik özellikleri bulmanıza yardımcı olması için bu tabloyu kullanın.  
  
|Ayar|Özellikler|  
|-------------|--------------|  
|Taşıma|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Noktadan noktaya güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Donanım hızlandırma<br /><br /> Yüksek aktarım hızı<br /><br /> Güvenli güvenlik duvarı<br /><br /> Yüksek gecikmeli uygulamalar<br /><br /> Birden çok atlama arasında yeniden şifreleme|  
|`Message`|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Baştan sona güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Zengin talep<br /><br /> Federasyon<br /><br /> Çok faktörlü kimlik doğrulaması<br /><br /> Özel belirteçler<br /><br /> Notary/zaman damgası hizmeti<br /><br /> Yüksek gecikmeli uygulamalar<br /><br /> İleti imzası kalıcılığı|  
|TransportWithMessageCredential|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Noktadan noktaya güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Donanım hızlandırma<br /><br /> Yüksek aktarım hızı<br /><br /> Zengin istemci talep<br /><br /> Federasyon<br /><br /> Çok faktörlü kimlik doğrulaması<br /><br /> Özel belirteçler<br /><br /> Güvenli güvenlik duvarı<br /><br /> Yüksek gecikmeli uygulamalar<br /><br /> Birden çok atlama arasında yeniden şifreleme|  
  
 Aşağıdaki tabloda, çeşitli modu ayarları destekleyen bağlamaları listelenmektedir. Tablo Hizmeti uç noktanızı oluşturmak için kullanılacak bir bağlamayı seçin.  
  
|Bağlama|Aktarım modu desteği|İleti modu desteği|TransportWithMessageCredential desteği|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|Evet|Evet|Evet|  
|`WSHttpBinding`|Evet|Evet|Evet|  
|`WSDualHttpBinding`|Hayır|Evet|Hayır|  
|`NetTcpBinding`|Evet|Evet|Evet|  
|`NetNamedPipeBinding`|Evet|Hayır|Hayır|  
|`NetMsmqBinding`|Evet|Evet|Hayır|  
|`MsmqIntegrationBinding`|Evet|Hayır|Hayır|  
|`wsFederationHttpBinding`|Hayır|Evet|Evet|  
  
## <a name="transport-credentials-in-bindings"></a>Bağlamaları aktarım kimlik bilgileri  
 Aşağıdaki tabloda kullanılabilir istemci kimlik bilgisi türlerinin ya da kullanırken listeler `BasicHttpBinding` veya `WSHttpBinding` Aktarım güvenlik modu.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|Yok.|İstemci mevcut herhangi bir kimlik bilgisi gerekmez belirtir. Bu, anonim bir istemciye dönüşür.|  
|Temel|Temel kimlik doğrulaması. Daha fazla bilgi için HTTP kimlik doğrulaması RFC 2617 – bakın: Temel ve Özet kimlik doğrulaması, kullanılabilir <https://go.microsoft.com/fwlink/?LinkId=84023>.|  
|Özet|Özet kimlik doğrulaması. Daha fazla bilgi için HTTP kimlik doğrulaması RFC 2617 – bakın: Temel ve Özet kimlik doğrulaması, kullanılabilir <https://go.microsoft.com/fwlink/?LinkId=84023>.|  
|NTLM|NT LAN Manager (NTLM) kimlik doğrulaması.|  
|Windows|Windows kimlik doğrulaması.|  
|Sertifika|Kimlik doğrulaması, bir sertifika kullanılarak gerçekleştirilir.|  
|IssuedToken|Gerekli izin verir, istemci kimlik doğrulaması ile veya bir güvenlik belirteci hizmeti tarafından verilmiş bir belirteç kullanarak [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Daha fazla bilgi için [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>İleti bağlamaları istemci kimlik bilgileri  
 Aşağıdaki tabloda bir bağlama ileti güvenlik modunda kullanırken kullanılabilir istemci kimlik bilgisi türlerini listeler.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|Yok.|Anonim istemci ile etkileşim kurmak hizmet sağlar.|  
|Windows|Windows kimlik bilgisi kimliği doğrulanmış bağlamında yapılması SOAP ileti alışverişlerinde sağlar.|  
|UserName|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir kullanıcı adı kimlik bilgisi. Güvenlik modu ayarlandığında unutmayın `TransportWithMessageCredential`, WCF parola ve bu anahtarları kullanarak ileti modu güvenliği için Özet veya türetme anahtarı parola gönderme desteklemez. Bu nedenle, WCF aktarma kullanıcı adı kimlik bilgilerini kullanarak güvenli zorlar.|  
|Sertifika|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir sertifika.|  
|IssuedToken|Özel belirteç sağlamak için bir güvenlik belirteci hizmeti kullanmak için hizmet verir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Bilgisi Türü Seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Güvenlik Davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
