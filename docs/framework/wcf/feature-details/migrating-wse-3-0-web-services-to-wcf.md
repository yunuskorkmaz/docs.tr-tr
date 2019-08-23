---
title: WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 5f615af0340a68e43a184465ff99637e5e5e06c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965323"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
WSE 3,0 Web hizmetlerini Windows Communication Foundation (WCF) geçişinin avantajları, gelişmiş performans ve ek aktarımlar, ek güvenlik senaryoları ve WS-* belirtimleri desteği içerir. WVA3,0 'den WCF 'ye geçirilen bir Web hizmeti,% 400 200 ' e varan performans geliştirmesine kadar. WCF tarafından desteklenen aktarımlar hakkında daha fazla bilgi için bkz. [bir taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). WCF tarafından desteklenen senaryoların listesi için bkz. [ortak güvenlik senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). WCF tarafından desteklenen belirtimlerin listesi için bkz. [Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Aşağıdaki bölümlerde, bir WVA3,0 Web hizmeti 'nin belirli bir özelliğinin WCF 'ye nasıl geçirileceğiyle ilgili yönergeler sağlanmaktadır.  
  
## <a name="general"></a>Genel  
 WVA3,0 ve WCF uygulamaları, hat düzeyinde birlikte çalışabilirlik ve ortak bir terminoloji kümesi içerir. WVA3,0 ve WCF uygulamaları, her ikisinin de desteklediği WS-* belirtimleri kümesine bağlı olarak, hat düzeyinde birlikte çalışabilir. Bir WCE 3,0 veya WCF uygulaması geliştirildiğinde, Wo 'da anahtar güvenlik onayları ve kimlik doğrulama modları gibi ortak bir terminoloji kümesi vardır.  
  
 WCF ve ASP.NET ya da WSE 3,0 programlama modelleri arasında birçok benzer yönü olsa da, bunlar farklıdır. WCF programlama modeli hakkında daha fazla bilgi için bkz. [temel programlama yaşam döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> Bir Wo Web hizmetini WCF 'ye geçirmek için, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı bir istemci oluşturmak için kullanılabilir. Bununla birlikte, bu istemci, WCF hizmeti için bir başlangıç noktası olarak kullanılabilecek arabirimler ve sınıflar içerir. Oluşturulan arabirimlerin <xref:System.ServiceModel.OperationContractAttribute> <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliği olarak `*`ayarlanmış olan sözleşmenin üyelerine uygulanmış özniteliği vardır. Bir Wo istemcisi bu ayarla bir Web hizmetini çağırdığında, aşağıdaki özel durum oluşur: **Web. Services3. ResponseProcessingException: WSE910: Yanıt iletisi işlenirken bir hata oluştu ve hatayı iç özel**durumda bulabilirsiniz. <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> Bunu azaltmak için, <xref:System.ServiceModel.OperationContractAttribute> `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`özniteliğinin özelliğini gibi değeri olmayan bir değere ayarlayın.`null`  
  
## <a name="security"></a>Güvenlik  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Bir ilke dosyası kullanılarak güvenliği sağlanan WVA3,0 Web Hizmetleri  
 WCF Hizmetleri, bir hizmetin güvenliğini sağlamak için bir yapılandırma dosyası kullanabilir ve bu mekanizma bir WSE 3,0 ilke dosyasına benzer. Wo 3,0 ' de bir ilke dosyası kullanarak bir Web hizmetini güvenli hale getirirken, anahtar onaylama güvenlik onayı veya özel bir ilke onaylama kullanırsınız. Anahtar güvenlik onayları, bir WCF güvenlik bağlama öğesinin kimlik doğrulama moduna yakından eşlenir. Aynı veya benzer şekilde adlandırılan WCF kimlik doğrulama modları ve WVA3,0 anahtar güvenlik onayları, aynı kimlik bilgisi türlerini kullanarak iletileri güvenli hale getirmeye yönelik değildir. Örneğin, `usernameForCertificate` wva3,0 'de anahtar onaylama güvenlik onayı, WCF 'de `UsernameForCertificate` kimlik doğrulama moduyla eşlenir. Aşağıdaki kod örnekleri, Wo 3,0 ' de anahtar güvenlik onayını `usernameForCertificate` kullanan en az bir ilkenin, özel bir bağlamada WCF 'de `UsernameForCertificate` bir kimlik doğrulama moduna nasıl eşlendiğini göstermektedir.  
  
 **WVA3,0**  
  
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
  
 İlke dosyasında belirtilen bir WVA3,0 Web hizmetinin güvenlik ayarlarını WCF 'ye geçirmek için bir yapılandırma dosyasında özel bir bağlama oluşturulmalıdır ve anahtar güvenlik onayı, eşdeğer kimlik doğrulama moduna ayarlanmalıdır. Ek olarak, WVAW 3,0 istemcileri hizmetle iletişim kurduğunda, özel bağlama, Ağustos 2004 WS-Addressing belirtimini kullanacak şekilde yapılandırılmalıdır. Geçirilen WCF hizmeti WVACE 3,0 istemcileriyle iletişim gerektirmez ve yalnızca güvenlik eşliği sağlamak zorunda kalmadan, özel bir bağlama oluşturmak yerine uygun güvenlik ayarlarıyla WCF sistem tarafından tanımlanan bağlamaları kullanmayı göz önünde bulundurun.  
  
 Aşağıdaki tabloda, bir WVA3,0 ilke dosyası ile WCF 'deki eşdeğer özel bağlama arasındaki eşleme listelenmektedir.  
  
|WVA3,0 anahtar güvenlik onayı|WCF özel bağlama yapılandırması|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF 'de özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Uygulama kodu kullanılarak güvenliği sağlanan WVA3,0 Web Hizmetleri  
 WVA3,0 veya WCF 'nin kullanılıp kullanılmadığını, güvenlik gereksinimlerinin yapılandırma yerine uygulama kodunda belirlenebilir. Wva3,0 'de, bu, `Policy` sınıfından türetilen bir sınıf oluşturularak ve sonra `Add` yöntemi çağırarak gereksinimleri ekleyerek gerçekleştirilir. Kodda güvenlik gereksinimlerini belirtme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir Ilke dosyası](https://go.microsoft.com/fwlink/?LinkId=73747)kullanmadan bir Web hizmetinin güvenliğini sağlama. WCF 'de, kodda güvenlik gereksinimlerini belirtmek için, <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının bir örneğini oluşturun ve ' a bir <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.BindingElementCollection>örneğini ekleyin. Güvenlik onaylama gereksinimleri, <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfının statik kimlik doğrulama modu yardımcı yöntemleri kullanılarak ayarlanır. WCF kullanarak kodda güvenlik gereksinimlerini belirtme hakkında daha fazla bilgi için bkz [. nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) kullanarak özel bağlama oluşturun ve [şunları yapın: Belirtilen kimlik doğrulama modu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)için bir SecurityBindingElement oluşturun.  
  
### <a name="wse-30-custom-policy-assertion"></a>WVA3,0 özel Ilke onaylama  
 WVA3,0 'de, iki tür özel ilke onaylamaları vardır: bir SOAP iletisini güvenli hale getirme ve bir SOAP iletisini güvenli hale getirme. SOAP iletilerinin güvenliğini sağlayan ilke onayları, wva3,0 `SecurityPolicyAssertion` sınıfından türetilir ve WCF <xref:System.ServiceModel.Channels.SecurityBindingElement> 'de kavramsal eşdeğer bir sınıftır.  
  
 Önemli bir noktaya dikkat edin, WVA3,0 anahtar güvenlik onayları, WCF kimlik doğrulama modlarının bir alt kümesidir. Wo 3,0 ' de özel bir ilke onayı oluşturduysanız, eşdeğer bir WCF kimlik doğrulama modu olabilir. Örneğin, wva3,0, anahtar güvenlik onayı ile `UsernameOverTransport` eşdeğer olan, ancak istemci kimlik doğrulaması amacıyla bir X. 509.440 sertifikası kullanan bir CertificateOverTransport güvenlik onayı sağlamaz. Bu senaryo için kendi özel ilke onayınız tanımlıyorsanız, WCF geçişi basit hale getirir. WCF, bu senaryo için bir kimlik doğrulama modu tanımlar, bu nedenle bir WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>yapılandırmak için statik kimlik doğrulama modu yardımcı yöntemlerinden yararlanabilirsiniz.  
  
 SOAP iletilerinin güvenliğini sağlayan özel bir ilke onaylaması ile eşdeğer olan bir WCF kimlik doğrulama modu olmadığında, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF sınıflarından bir sınıf türetir ve eşdeğer bağlama öğesini belirtin. Daha ayrıntılı bilgi için bkz [. nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)kullanarak özel bir bağlama oluşturun.  
  
 Bir SOAP iletisini güvenli hale getirmeye yönelik özel bir ilke onayını dönüştürmek için, bkz. [filtreleme](../../../../docs/framework/wcf/feature-details/filtering.md) ve örnek [özel ileti yakalayıcısı](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>WVA3,0 özel güvenlik belirteci  
 Özel belirteç oluşturmak için WCF programlama modeli WVA3,0 'den farklıdır. Wo 'da özel belirteç oluşturma hakkında ayrıntılı bilgi için bkz. [özel güvenlik belirteçleri oluşturma](https://go.microsoft.com/fwlink/?LinkID=73750). WCF 'de özel belirteç oluşturma hakkında ayrıntılı bilgi için bkz [. nasıl yapılır: Özel bir belirteç](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)oluşturun.  
  
### <a name="wse-30-custom-token-manager"></a>WVA3,0 özel belirteç Yöneticisi  
 Özel belirteç Yöneticisi oluşturmaya yönelik programlama modeli, WCF 'de WVA3,0 'den farklıdır. Özel bir belirteç Yöneticisi ve özel bir güvenlik belirteci için gereken diğer bileşenleri oluşturma hakkında ayrıntılı bilgi için bkz [. nasıl yapılır: Özel bir belirteç](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)oluşturun.  
  
> [!NOTE]
> Özel `UsernameToken` bir güvenlik belirteci Yöneticisi oluşturduysanız, WCF özel bir güvenlik belirteci Yöneticisi oluşturmaktan kimlik doğrulama mantığını belirtmek için daha kolay bir mekanizma sağlar. Daha ayrıntılı bilgi için bkz [. nasıl yapılır: Özel bir Kullanıcı adı ve parola doğrulayıcısı](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)kullanın.  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM kodlamalı SOAP iletileri kullanan WVA3,0 Web Hizmetleri  
 Bir WVAM 3 uygulaması gibi, bir WCF uygulaması, yapılandırmada MTOM ileti kodlamasını belirtebilir. Bu ayarı geçirmek için, [ \<MtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) hizmetin bağlamasına ekleyin. Aşağıdaki kod örneği, WCF ile eşdeğer bir hizmetin WVA3,0 ' de MTOM kodlamasının nasıl belirtildiğini gösterir.  
  
 **WVA3,0**  
  
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
  
## <a name="messaging"></a>İleti  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WVAW Ileti API 'sini kullanan wva3,0 uygulamaları  
 WVAW mesajlaşma API 'SI, istemci ve Web hizmeti arasında iletilen XML 'e doğrudan erişim elde etmek için kullanıldığında, uygulama "düz eski XML" (POX) kullanacak şekilde dönüştürülebilirler. POX hakkında daha fazla bilgi için bkz. [POX Uygulamaları Ile birlikte çalışabilirlik](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). WVAW mesajlaşma API 'SI hakkında daha fazla bilgi için bkz. [WVAMESAJLAŞMA API kullanarak soap Iletileri gönderme ve alma](https://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Taşımalar  
  
### <a name="tcp"></a>TCP  
 Varsayılan olarak, TCP taşıyıcısı kullanılarak SOAP iletileri gönderen WVA3,0 istemcileri ve Web Hizmetleri, WCF istemcileri ve Web hizmetleriyle birlikte çalışmaz. Bu uyumsuzluğun nedeni, TCP protokolünde kullanılan çerçeveleme ve performans nedenleriyle farklılıklardır. Ancak, bir WCF örneği WVA3,0 ile birlikte çalışan özel bir TCP oturumunun nasıl uygulanacağını ayrıntılarıyla açıklamaktadır. Bu örnekle ilgili ayrıntılar için bkz [. taşıma: WVA3,0 TCP birlikte](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)çalışabilirliği.  
  
 Bir WCF uygulamasının TCP aktarımını kullandığını belirtmek için [ \<NetTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)kullanın.  
  
### <a name="custom-transport"></a>Özel aktarım  
 WCF 'de bir WVA3,0 özel taşımanın eşdeğeri bir kanal uzantısıdır. Kanal uzantısı oluşturma hakkında ayrıntılı bilgi için bkz. [Kanal Katmanını Genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Programlama Yaşam Döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen kimlik doğrulama modu için bir SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
