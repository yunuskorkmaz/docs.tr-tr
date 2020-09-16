---
title: WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: c7feac0a44883e8019acfeaa288752fb051c667f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554097"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
WSE 3,0 Web hizmetlerini Windows Communication Foundation (WCF) geçişinin avantajları, gelişmiş performans ve ek aktarımlar, ek güvenlik senaryoları ve WS-* belirtimleri desteği içerir. WVA3,0 'den WCF 'ye geçirilen bir Web hizmeti, %400 200 ' e varan performans geliştirmesine kadar. WCF tarafından desteklenen aktarımlar hakkında daha fazla bilgi için bkz. [bir taşıma seçme](choosing-a-transport.md). WCF tarafından desteklenen senaryoların listesi için bkz. [ortak güvenlik senaryoları](common-security-scenarios.md). WCF tarafından desteklenen belirtimlerin listesi için bkz. [Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu](web-services-protocols-interoperability-guide.md).  
  
 Aşağıdaki bölümlerde, bir WVA3,0 Web hizmeti 'nin belirli bir özelliğinin WCF 'ye nasıl geçirileceğiyle ilgili yönergeler sağlanmaktadır.  
  
## <a name="general"></a>Genel  
 WVA3,0 ve WCF uygulamaları, hat düzeyinde birlikte çalışabilirlik ve ortak bir terminoloji kümesi içerir. WVA3,0 ve WCF uygulamaları, her ikisinin de desteklediği WS-* belirtimleri kümesine bağlı olarak, hat düzeyinde birlikte çalışabilir. Bir WCE 3,0 veya WCF uygulaması geliştirildiğinde, Wo 'da anahtar güvenlik onayları ve kimlik doğrulama modları gibi ortak bir terminoloji kümesi vardır.  
  
 WCF ve ASP.NET ya da WSE 3,0 programlama modelleri arasında birçok benzer yönü olsa da, bunlar farklıdır. WCF programlama modeli hakkında daha fazla bilgi için bkz. [temel programlama yaşam döngüsü](../basic-programming-lifecycle.md).  
  
> [!NOTE]
> Bir Wo Web hizmetini WCF 'ye geçirmek için, [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracı bir istemci oluşturmak için kullanılabilir. Bununla birlikte, bu istemci, WCF hizmeti için bir başlangıç noktası olarak kullanılabilecek arabirimler ve sınıflar içerir. Oluşturulan arabirimlerin <xref:System.ServiceModel.OperationContractAttribute> özelliği olarak ayarlanmış olan sözleşmenin üyelerine uygulanmış özniteliği vardır <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> `*` . Bir Wo istemcisi bu ayarla bir Web hizmetini çağırdığında, şu özel durum atılır: **Web. Services3. ResponseProcessingException: WSE910: yanıt iletisi işlenirken bir hata oluştu ve hatayı iç özel durumda bulabilirsiniz**. Bunu azaltmak için, <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> <xref:System.ServiceModel.OperationContractAttribute> özniteliğinin özelliğini `null` gibi değeri olmayan bir değere ayarlayın `http://Microsoft.WCF.Documentation/ResponseToOCAMethod` .  
  
## <a name="security"></a>Güvenlik  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Bir ilke dosyası kullanılarak güvenliği sağlanan WVA3,0 Web Hizmetleri  
 WCF Hizmetleri, bir hizmetin güvenliğini sağlamak için bir yapılandırma dosyası kullanabilir ve bu mekanizma bir WSE 3,0 ilke dosyasına benzer. Wo 3,0 ' de bir ilke dosyası kullanarak bir Web hizmetini güvenli hale getirirken, anahtar onaylama güvenlik onayı veya özel bir ilke onaylama kullanırsınız. Anahtar güvenlik onayları, bir WCF güvenlik bağlama öğesinin kimlik doğrulama moduna yakından eşlenir. Aynı veya benzer şekilde adlandırılan WCF kimlik doğrulama modları ve WVA3,0 anahtar güvenlik onayları, aynı kimlik bilgisi türlerini kullanarak iletileri güvenli hale getirmeye yönelik değildir. Örneğin, `usernameForCertificate` wva3,0 'de anahtar onaylama güvenlik onayı, `UsernameForCertificate` WCF 'de kimlik doğrulama moduyla eşlenir. Aşağıdaki kod örnekleri, `usernameForCertificate` wo 3,0 ' de anahtar güvenlik onayını kullanan en az bir ilkenin, `UsernameForCertificate` Özel BIR bağlamada WCF 'de bir kimlik doğrulama moduna nasıl eşlendiğini göstermektedir.  
  
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
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF 'de özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Uygulama kodu kullanılarak güvenliği sağlanan WVA3,0 Web Hizmetleri  
 WVA3,0 veya WCF 'nin kullanılıp kullanılmadığını, güvenlik gereksinimlerinin yapılandırma yerine uygulama kodunda belirlenebilir. WVA3,0 'de, bu, sınıfından türetilen bir sınıf oluşturularak `Policy` ve sonra yöntemi çağırarak gereksinimleri ekleyerek gerçekleştirilir `Add` . Kodda güvenlik gereksinimlerini belirtme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir Web hizmetini bir Ilke dosyası kullanmadan güvenli hale getirme](/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). WCF 'de, kodda güvenlik gereksinimlerini belirtmek için, sınıfının bir örneğini oluşturun <xref:System.ServiceModel.Channels.BindingElementCollection> ve ' a bir örneğini ekleyin <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.BindingElementCollection> . Güvenlik onaylama gereksinimleri, sınıfının statik kimlik doğrulama modu yardımcı yöntemleri kullanılarak ayarlanır <xref:System.ServiceModel.Channels.SecurityBindingElement> . WCF kullanarak kodda güvenlik gereksinimlerini belirtme hakkında daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md) ve [nasıl yapılır: belirtilen bir kimlik doğrulama modu Için bir SecurityBindingElement oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>WVA3,0 özel Ilke onaylama  
 WVA3,0 'de, iki tür özel ilke onaylamaları vardır: bir SOAP iletisini güvenli hale getirme ve bir SOAP iletisini güvenli hale getirme. SOAP iletilerinin güvenliğini sağlayan ilke onayları, WVA3,0 `SecurityPolicyAssertion` sınıfından türetilir ve WCF 'de kavramsal eşdeğer bir <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıftır.  
  
 Önemli bir noktaya dikkat edin, WVA3,0 anahtar güvenlik onayları, WCF kimlik doğrulama modlarının bir alt kümesidir. Wo 3,0 ' de özel bir ilke onayı oluşturduysanız, eşdeğer bir WCF kimlik doğrulama modu olabilir. Örneğin, WVA3,0, `UsernameOverTransport` anahtar güvenlik onayı ile eşdeğer olan, ancak istemci kimlik doğrulaması amacıyla bir X. 509.440 sertifikası kullanan bir CertificateOverTransport güvenlik onayı sağlamaz. Bu senaryo için kendi özel ilke onayınız tanımlıyorsanız, WCF geçişi basit hale getirir. WCF, bu senaryo için bir kimlik doğrulama modu tanımlar, bu nedenle bir WCF yapılandırmak için statik kimlik doğrulama modu yardımcı yöntemlerinden yararlanabilirsiniz <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
 SOAP iletilerinin güvenliğini sağlayan özel bir ilke onaylaması ile eşdeğer olan bir WCF kimlik doğrulama modu olmadığında, veya WCF sınıflarından bir sınıf türetir <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ve eşdeğer bağlama öğesini belirtin. Daha ayrıntılı bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Bir SOAP iletisini güvenli hale getirmeye yönelik özel bir ilke onayını dönüştürmek için, bkz. [filtreleme](filtering.md) ve örnek [özel ileti yakalayıcısı](../samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>WVA3,0 özel güvenlik belirteci  
 Özel belirteç oluşturmak için WCF programlama modeli WVA3,0 'den farklıdır. Wo 'da özel belirteç oluşturma hakkında ayrıntılı bilgi için bkz. [özel güvenlik belirteçleri oluşturma](/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). WCF 'de özel belirteç oluşturma hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: özel belirteç oluşturma](../extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WVA3,0 özel belirteç Yöneticisi  
 Özel belirteç Yöneticisi oluşturmaya yönelik programlama modeli, WCF 'de WVA3,0 'den farklıdır. Özel bir belirteç Yöneticisi ve özel bir güvenlik belirteci için gereken diğer bileşenleri oluşturma hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: özel belirteç oluşturma](../extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Özel bir `UsernameToken` güvenlik belirteci Yöneticisi oluşturduysanız, WCF özel bir güvenlik belirteci Yöneticisi oluşturmaktan kimlik doğrulama mantığını belirtmek için daha kolay bir mekanizma sağlar. Daha ayrıntılı bilgi için bkz. [nasıl yapılır: özel Kullanıcı adı ve parola doğrulayıcısı kullanma](how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM kodlamalı SOAP iletileri kullanan WVA3,0 Web Hizmetleri  
 Bir WVAM 3 uygulaması gibi, bir WCF uygulaması, yapılandırmada MTOM ileti kodlamasını belirtebilir. Bu ayarı geçirmek için, [\<mtomMessageEncoding>](../../configure-apps/file-schema/wcf/mtommessageencoding.md) hizmetini bağlamaya ekleyin. Aşağıdaki kod örneği, WCF ile eşdeğer bir hizmetin WVA3,0 ' de MTOM kodlamasının nasıl belirtildiğini gösterir.  
  
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
  
## <a name="messaging"></a>Mesajlaşma  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WVAW Ileti API 'sini kullanan wva3,0 uygulamaları  

 WVAW mesajlaşma API 'SI, istemci ve Web hizmeti arasında iletilen XML 'e doğrudan erişim elde etmek için kullanıldığında, uygulama "düz eski XML" (POX) kullanacak şekilde dönüştürülebilirler. POX hakkında daha fazla bilgi için bkz. [POX Uygulamaları Ile birlikte çalışabilirlik](interoperability-with-pox-applications.md). WVAW mesajlaşma API 'SI hakkında daha fazla bilgi için bkz. [WVAMESAJLAŞMA API kullanarak soap Iletileri gönderme ve alma](/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Taşımalar  
  
### <a name="tcp"></a>TCP  
 Varsayılan olarak, TCP taşıyıcısı kullanılarak SOAP iletileri gönderen WVA3,0 istemcileri ve Web Hizmetleri, WCF istemcileri ve Web hizmetleriyle birlikte çalışmaz. Bu uyumsuzluğun nedeni, TCP protokolünde kullanılan çerçeveleme ve performans nedenleriyle farklılıklardır. Ancak, bir WCF örneği WVA3,0 ile birlikte çalışan özel bir TCP oturumunun nasıl uygulanacağını ayrıntılarıyla açıklamaktadır. Bu örnekle ilgili ayrıntılar için bkz. [Transport: wva3,0 TCP birlikte çalışabilirliği](../samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Bir WCF uygulamasının TCP aktarımını kullandığını belirtmek için, kullanın [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) .  
  
### <a name="custom-transport"></a>Özel aktarım  
 WCF 'de bir WVA3,0 özel taşımanın eşdeğeri bir kanal uzantısıdır. Kanal uzantısı oluşturma hakkında ayrıntılı bilgi için bkz. [Kanal Katmanını Genişletme](../extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Programlama Yaşam Döngüsü](../basic-programming-lifecycle.md)
- [Özel Bağlamalar](../extending/custom-bindings.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
