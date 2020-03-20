---
title: WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184576"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
WSE 3.0 Web hizmetlerini Windows Communication Foundation'a (WCF) geçirmenin avantajları arasında gelişmiş performans ve ek aktarımların desteklenmesi, ek güvenlik senaryoları ve WS-* belirtimleri yer alır. WSE 3.0'dan WCF'ye geçirilen bir Web hizmetinde %200 ila %400 arasında performans artışı yaşayabilir. WCF tarafından desteklenen taşımalar hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) WCF tarafından desteklenen senaryoların listesi için [Bkz. Ortak Güvenlik Senaryoları.](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md) WCF tarafından desteklenen belirtimlerin listesi için [Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu'na](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)bakın.  
  
 Aşağıdaki bölümler, WSE 3.0 Web hizmetinin belirli bir özelliğinin WCF'ye nasıl geçirileceğe ilişkin kılavuzlar sağlar.  
  
## <a name="general"></a>Genel  
 WSE 3.0 ve WCF uygulamaları, kablo düzeyinde birlikte çalışabilirlik ve yaygın bir terminoloji kümesi içerir. WSE 3.0 ve WCF uygulamaları, her ikisinin de desteklediği WS-* spesifikasyonları kümesine göre kablo düzeyinde birlikte çalışabilir. Bir WSE 3.0 veya WCF uygulaması geliştirildiğinde, WSE'deki anahtar teslim güvenlik iddialarının adları ve kimlik doğrulama modları gibi ortak bir terminoloji kümesi vardır.  
  
 WCF ve ASP.NET veya WSE 3.0 programlama modelleri arasında benzer birçok yönü olmasına rağmen, bunlar farklıdır. WCF programlama modeli hakkında ayrıntılı bilgi için [Temel Programlama Yaşam Döngüsü'ne](../../../../docs/framework/wcf/basic-programming-lifecycle.md)bakın.  
  
> [!NOTE]
> WSE Web hizmetini WCF'ye geçirmek için [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı istemci oluşturmak için kullanılabilir. Ancak bu istemci, bir WCF hizmeti için de başlangıç noktası olarak kullanılabilecek arabirimler ve sınıflar içerir. Oluşturulan arabirimler, '' <xref:System.ServiceModel.OperationContractAttribute> olarak <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> `*`ayarlanan özellik ile sözleşme üyelerine uygulanan öznitelik vardır. Bir WSE istemcisi bu ayarı içeren bir Web hizmetini aradığında, aşağıdaki özel durum atılır: **Web.Services3.ResponseProcessingException: WSE910: Yanıt iletisinin işlenmesi sırasında bir hata oluştu ve hatayı iç özel durum içinde bulabilirsiniz.** Bunu azaltmak <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> için, özniteliğin özelliğini <xref:System.ServiceModel.OperationContractAttribute> değer olmayan`null` bir değere `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`ayarlayın.  
  
## <a name="security"></a>Güvenlik  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Bir ilke dosyası kullanılarak güvenli WSE 3.0 Web hizmetleri  
 WCF hizmetleri bir hizmeti güvence altına almak için bir yapılandırma dosyası kullanabilir ve bu mekanizma WSE 3.0 ilke dosyasına benzer. WSE 3.0'da bir web hizmetini bir ilke dosyası kullanarak güvence altına alırken, anahtar teslimi güvenlik iddiası veya özel bir ilke iddiası kullanırsınız. Anahtar teslimgüvenlik iddiaları, wcf güvenlik bağlama öğesinin kimlik doğrulama moduna yakından eşler. WCF kimlik doğrulama modları ve WSE 3.0 anahtar teslimi güvenlik iddiaları aynı veya benzer olarak adlandırılır, onlar aynı kimlik bilgisi türlerini kullanarak iletileri güvenli. Örneğin, WSE 3.0 eşlemlerinde WCF'deki `usernameForCertificate` `UsernameForCertificate` kimlik doğrulama moduna anahtar teslim güvenlik iddiası. Aşağıdaki kod örnekleri, WSE 3.0 `usernameForCertificate` eşlemlerinde anahtar teslim güvenlik iddiasını `UsernameForCertificate` kullanan en küçük bir ilkenin wcf'deki bir kimlik doğrulama moduna nasıl özel bir bağlama yla geldiğini gösterir.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Bir ilke dosyasında belirtilen bir WSE 3.0 Web hizmetinin güvenlik ayarlarını WCF'ye geçirmek için yapılandırma dosyasında özel bir bağlama oluşturulması ve anahtar teslimgüvenlik lisasının eşdeğer kimlik doğrulama moduna ayarlanması gerekir. Ayrıca, WSE 3.0 istemcileri hizmetle iletişim kurduğunda, özel bağlamanın Ağustos 2004 WS Adresleme belirtimini kullanacak şekilde yapılandırılması gerekir. Geçirilen WCF hizmeti WSE 3.0 istemcileriyle iletişim gerektirmediğinde ve yalnızca güvenlik eşitliğini korumanız gerektiğinde, özel bir bağlama oluşturmak yerine WCF sistemi tanımlı bağlamaları uygun güvenlik ayarlarıyla kullanmayı düşünün.  
  
 Aşağıdaki tabloda, WSE 3.0 ilke dosyası ile WCF'deki eşdeğer özel bağlama arasındaki eşleme listelenir.  
  
|WSE 3.0 Anahtar Teslim Güvenlik İddiası|WCF özel bağlama yapılandırması|  
|----------------------------------------|--------------------------------------|  
|\<kullanıcı adıOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Güvenlik />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kullanıcı adıForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonimForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF'de özel bağlamalar oluşturma hakkında daha fazla bilgi için Bkz. [Özel Bağlamalar.](../../../../docs/framework/wcf/extending/custom-bindings.md)  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Uygulama kodu kullanılarak güvenli WSE 3.0 Web hizmetleri  
 WSE 3.0 veya WCF kullanılıp kullanılmadığı, güvenlik gereksinimleri yapılandırma yerine uygulama kodunda belirtilebilir. WSE 3.0'da bu, `Policy` sınıftan türetilen bir sınıf oluşturularak ve `Add` ardından yöntemi çağırarak gereksinimleri ekleyerek gerçekleştirilir. Koddaki güvenlik gereksinimlerini belirtme hakkında daha fazla bilgi için [bkz: İlke Dosyasını Kullanmadan Web Hizmetini Güvenli Hale](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10))Getirin. WCF'de, koddaki güvenlik gereksinimlerini belirtmek için <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfın bir örneğini <xref:System.ServiceModel.Channels.SecurityBindingElement> oluşturun <xref:System.ServiceModel.Channels.BindingElementCollection>ve bir .'e bir örnek ekleyin. Güvenlik sadansı gereksinimleri <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfın statik kimlik doğrulama modu yardımcı yöntemleri kullanılarak ayarlanır. WCF kullanarak kodda güvenlik gereksinimlerini belirtme hakkında daha fazla bilgi için [bkz: SecurityBindingElement'i Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md) ve Nasıl [Yapılacağını: Belirtilen Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 Özel İlke İddiası  
 WSE 3.0'da iki tür özel ilke iddiası vardır: SOAP iletisini güvence altına alan ve SOAP iletisini güvence altına almayanlar. SOAP iletilerini güvenli hale getiren ilke iddiaları `SecurityPolicyAssertion` WSE 3.0 sınıfından <xref:System.ServiceModel.Channels.SecurityBindingElement> türemiştir ve WCF'deki kavramsal eşdeğer sınıftır.  
  
 Dikkat edilmesi gereken önemli bir nokta, WSE 3.0 anahtar teslimi güvenlik iddialarının WCF kimlik doğrulama modlarının bir alt kümesi olmasıdır. WSE 3.0'da özel bir ilke belirleme oluşturduysanız, eşdeğer bir WCF kimlik doğrulama modu olabilir. Örneğin, WSE 3.0 anahtar teslimi güvenlik iddiası eşdeğer `UsernameOverTransport` bir CertificateOverTransport güvenlik iddiası sağlamaz, ancak istemci kimlik doğrulaması amaçları için bir X.509 sertifikası kullanır. Bu senaryo için kendi özel ilke iddianızı tanımladıysanız, WCF geçişi kolaylaştırır. WCF bu senaryo için bir kimlik doğrulama modu tanımlar, böylece bir WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>yapılandırmak için statik kimlik doğrulama modu yardımcı yöntemlerinden yararlanabilirsiniz.  
  
 SOAP iletilerini güvence altına alan özel bir ilke ilkesine eşdeğer bir WCF kimlik <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>doğrulama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>modu olmadığında, bir sınıf türetin veya WCF sınıfları ve eşdeğer bağlama öğesi belirtin. Daha fazla ayrıntı [için bkz: SecurityBindingElement'i kullanarak Özel Bağlama Oluşturun.](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
  
 SOAP iletisini güvenli hale getiren özel bir ilke iddiasını dönüştürmek için [Filtreleme](../../../../docs/framework/wcf/feature-details/filtering.md) ve örnek [Özel İleti Durdurucu'ya](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)bakın.  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 Özel Güvenlik Belirteci  
 Özel bir belirteç oluşturmak için WCF programlama modeli WSE 3.0 farklıdır. WSE'de özel bir belirteç oluşturma hakkında ayrıntılı bilgi [için](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10))bkz. WCF'de özel bir belirteç oluşturma yla ilgili ayrıntılar için [bkz.](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 Özel Jeton Yöneticisi  
 Özel bir belirteç yöneticisi oluşturmak için programlama modeli WCF WSE 3.0 farklıdır. Özel bir belirteç yöneticisi ve özel güvenlik belirteci için gerekli olan diğer bileşenler in nasıl oluşturulabildiğini hakkında ayrıntılar için [bkz.](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
  
> [!NOTE]
> Özel `UsernameToken` bir güvenlik belirteç yöneticisi oluşturduysanız, WCF kimlik doğrulama mantığını belirtmek için özel bir güvenlik belirteç yöneticisi oluşturmaktan daha kolay bir mekanizma sağlar. Daha fazla bilgi [için bkz: Özel Kullanıcı Adı ve Şifre Doğrulayıcısı kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM kodlu SOAP iletileri kullanan WSE 3.0 Web hizmetleri  
 BIR WSE 3 uygulaması gibi, bir WCF uygulaması yapılandırmada MTOM ileti kodlama belirtebilir. Bu ayarı geçirmek için, [ \<hizmet](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) için bağlama için mtomMessageEncoding>ekleyin. Aşağıdaki kod örneği, WCF'de eşdeğer bir hizmet için MTOM kodlamasının WSE 3.0'da nasıl belirtildiğini gösterir.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Mesajlaşma  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE 3.0 WSE Mesajlaşma API'sini kullanan uygulamalar  

 WSE Mesajlaşma API istemci ve Web hizmeti arasında iletilen XML doğrudan erişim elde etmek için kullanıldığında, uygulama "Düz Eski XML" (POX) kullanmak için dönüştürülebilir. POX hakkında daha fazla bilgi [için, POX Uygulamaları ile Birlikte Çalışabilirlik'e](interoperability-with-pox-applications.md)bakın. WSE Mesajlaşma API'si hakkında daha fazla bilgi için [WSE Mesajlaşma API'sini kullanarak SOAP İletileri Gönderme ve Alma'ya](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10))bakın.  
  
## <a name="transports"></a>Taşımalar  
  
### <a name="tcp"></a>TCP  
 Varsayılan olarak, TCP aktarımını kullanarak SOAP iletileri gönderen WSE 3.0 istemcileri ve Web hizmetleri WCF istemcileri ve Web hizmetleriyle birlikte çalışmaz. Bu uyumsuzluk, TCP protokolünde kullanılan çerçevefarklılıklarından ve performans nedenlerinden kaynaklanmaktadır. Ancak, bir WCF örneği WSE 3.0 ile birlikte çalışan özel bir TCP oturumunun nasıl uygulanacağını ayrıntılarıyla anlatır. Bu örnekle ilgili ayrıntılar için [Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'e](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)bakın.  
  
 Bir WCF uygulamasının TCP aktarımını kullandığını belirtmek için [ \<netTcpBinding>' ](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)ı kullanın.  
  
### <a name="custom-transport"></a>Özel Taşıma  
 WCF'de WSE 3.0 özel taşımaeşdeğerbir kanal uzantısıdır. Kanal uzantısı oluşturma hakkında ayrıntılı bilgi için Kanal [Katmanını Genişletme bölümüne](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Programlama Yaşam Döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
