---
title: WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 21e36be178bb0dd0c52213d8c4c1387a564a0e5a
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539687"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
Gelişmiş performans ve Destek ek taşımaları, ek güvenlik senaryoları ve WS - geçirme WSE 3.0 Web Hizmetleri için Windows Communication Foundation (WCF) avantajlarını içerir * belirtimleri. WSE 3.0 uygulamasından WCF'ye geçirilen bir Web hizmeti, en fazla %200 %400 performans iyileştirmesi oluşabilir. WCF tarafından desteklenen aktarmalar hakkında daha fazla bilgi için bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). WCF tarafından desteklenen senaryolarla listesi için bkz. [ortak güvenlik senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). WCF tarafından desteklenen belirtimleri listesi için bkz. [Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Aşağıdaki bölümlerde, belirli bir özellik WSE 3.0 Web hizmetinin WCF'ye geçiş yapmaya yönelik rehberlik sağlar.  
  
## <a name="general"></a>Genel  
 WSE 3.0 ve WCF uygulamaları, hat düzeyinde birlikte çalışabilirlik ve terminolojisi ortak bir kümesini içerir. WSE 3.0 ve WCF uygulamalarını hat WS-kümesi temel alınarak düzeyinde birlikte çalışabilir olduğundan * belirtimlerini her ikisi de destekler. WSE 3.0 veya WCF bir uygulama geliştirdiğinizde, ortak terminoloji, kullanıma hazır güvenlik onaylar WSE ve kimlik doğrulama modları adları gibi birtakım yoktur.  
  
 Bunlar, ASP.NET ve WCF arasında birçok benzer yönden olsa veya programlama modellerini WSE 3.0, farklıdır. WCF programlama modeli hakkında daha fazla ayrıntı için bkz: [temel programlama yaşam döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  WSE Web hizmeti WCF'ye taşıma için [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı, bir istemci oluşturmak için kullanılabilir. Başlangıç olarak kullanılan sınıfları bir WCF hizmeti için çok noktası ve istemci ancak arabirimlerini içerir. Oluşturulan arabirimlere sahip <xref:System.ServiceModel.OperationContractAttribute> sözleşmeyle üyelerine uygulanan öznitelik <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliğini `*`. WSE istemci bu ayarı ile bir Web hizmeti çağırdığında, şu özel durum: **Web.Services3.ResponseProcessingException: WSE910: bir yanıt iletisi işlenirken bir hata oluştu ve içinde iç hata bulabilirsiniz özel durum**. Bunu azaltmak için ayarlanmış <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliği <xref:System.ServiceModel.OperationContractAttribute> özniteliği olmayan bir`null` gibi değerini `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Güvenlik  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Bir ilke dosyası kullanılarak güvenli hale getirilir WSE 3.0 Web Hizmetleri  
 Bir hizmeti güvenli hale getirme için bir yapılandırma dosyası WCF hizmetlerini kullanabilirsiniz ve bu mekanizma, bir WSE 3.0 ilkesi dosyasına benzer. WSE bir ilke dosyası kullanarak bir Web hizmeti güvenli hale getirirken 3.0 kullanıma hazır güvenlik onaylama işlemi ya da bir özel ilke onayı kullanın. Kullanıma hazır güvenlik onaylama WCF güvenlik bağlama öğesinin kimlik doğrulaması moduna yakından eşlenir. Yalnızca WCF kimlik doğrulama modları ve kullanıma hazır güvenlik onaylar WSE 3.0 aynı adlı veya benzer şekilde, bunlar aynı kimlik bilgisi türlerini kullanarak iletileri güvenli hale getirme. Örneğin, `usernameForCertificate` kullanıma hazır güvenlik onaylama işlemi WSE 3.0 eşlendiğini `UsernameForCertificate` wcf'de kimlik doğrulama modu. Aşağıdaki kod örnekleri kullanan bir ilke nasıl göstermek `usernameForCertificate` kullanıma hazır güvenlik onaylama işlemi WSE 3.0 eşlenen bir `UsernameForCertificate` özel bir bağlamaya wcf'de kimlik doğrulama modu.  
  
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
  
 WCF için bir ilke dosyasında belirtilen WSE 3.0 Web hizmeti güvenlik ayarlarını geçirmek için bir yapılandırma dosyasında özel bir bağlama oluşturulmalı ve kullanıma hazır güvenlik onaylama işlemi, eşdeğer bir kimlik doğrulaması moduna ayarlanmalıdır. Ayrıca, özel bağlama Ağustos 2004 kullanmak için yapılandırılmalıdır WSE 3.0 istemciler hizmetiyle iletişim kurduğunda WS-Addressing belirtimi. Geçirilen bir WCF Hizmeti WSE 3.0 istemcileriyle iletişim gerektirmez ve yalnızca güvenlik eşlik korumalıdır, sistem tarafından tanımlanan WCF bağlamaları ile özel bir bağlama oluşturmak yerine, uygun güvenlik ayarlarını kullanarak göz önünde bulundurun.  
  
 Aşağıdaki tabloda, WCF eşdeğer özel bağlama ile WSE 3.0 ilke dosyası arasında eşleme listeler.  
  
|WSE 3.0 kullanıma hazır güvenlik onaylama işlemi|WCF özel bağlama yapılandırma|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF'de özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Uygulama kodu kullanılarak güvenli hale getirilir WSE 3.0 Web Hizmetleri  
 WSE 3.0 veya WCF kullanılıp kullanılmayacağını güvenlik gereksinimlerini yerine uygulama kodu yapılandırma belirtilebilir. WSE 3.0 sürümünde, bu, türetilen bir sınıf oluşturularak gerçekleştirilir `Policy` sınıfı ve çağırarak gereksinimlerine göre ekleme `Add` yöntemi. Kod içinde güvenlik gereksinimlerini belirtme hakkında daha fazla ayrıntı için bkz. [nasıl yapılır: bir ilke dosyası kullanarak bir Web hizmeti olmadan güvenli](https://go.microsoft.com/fwlink/?LinkId=73747). WCF'de, kod içinde güvenlik gereksinimlerini belirtmek için bir örneğini oluşturun. <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve bir örneğini ekleme bir <xref:System.ServiceModel.Channels.SecurityBindingElement> için <xref:System.ServiceModel.Channels.BindingElementCollection>. Güvenlik onaylama işlemi gereksinimlerini statik kimlik doğrulama modu yardımcı yöntemleri kullanılarak ayarlanan <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. WCF kullanarak kod içinde güvenlik gereksinimlerini belirtme hakkında daha fazla ayrıntı için bkz. [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) ve [nasıl yapılır: bir belirtilen için SecurityBindingElement oluşturma Kimlik doğrulama modu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 özel ilke onaylama  
 WSE 3.0 içinde özel ilke onaylamalarını iki tür vardır: güvenli bir SOAP iletisi ve bir SOAP ileti güvenliğini o olanlar. SOAP iletilerini güvenli ilke onaylamalarını WSE 3.0 türetilen `SecurityPolicyAssertion` sınıfı ve WCF kavramsal eşdeğer <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.  
  
 Dikkat edilecek önemli bir nokta WSE 3.0 kullanıma hazır güvenlik onaylar WCF kimlik doğrulama modları kümesini olmasıdır. WSE 3.0 içinde bir özel ilke onaylama oluşturduysanız, eşdeğer bir WCF kimlik doğrulama modu olabilir. Örneğin, WSE 3.0 eş değeri olan bir CertificateOverTransport güvenlik onaylama işlemi sağlamaz `UsernameOverTransport` kullanıma hazır güvenlik onaylama işlemi, ancak istemci kimlik doğrulaması amacıyla bir X.509 sertifikası kullanır. Bu senaryo için kendi özel İlkesi onayını tanımladıysanız, WCF geçişi basitleştirir. WCF, statik kimlik doğrulamasının bir WCF yapılandırma modu yardımcı yöntemler böylece bu senaryo için bir kimlik doğrulama modu tanımlar<xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 SOAP iletilerini güvenliğini sağlar. bir özel ilke onaylama eşdeğerdir bir WCF kimlik doğrulama modu olmadığında öğesinden bir sınıf türetin <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF sınıfları ve eşdeğer bağlama öğesi belirtin. Daha fazla ayrıntı için [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 SOAP iletisi güvenli olmayan bir özel ilke onaylama dönüştürmek için bkz [filtreleme](../../../../docs/framework/wcf/feature-details/filtering.md) ve örnek [özel ileti kesici](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 özel güvenlik belirteci  
 Özel belirteç oluşturma için WCF programlama modeli WSE 3.0 farklıdır. WSE içinde özel belirteç oluşturma hakkında daha fazla bilgi için bkz: [özel güvenlik belirteçleri oluşturma](https://go.microsoft.com/fwlink/?LinkID=73750). WCF'de özel belirteç oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 özel belirteci yöneticisi  
 Özel bir belirteci yöneticisi oluşturmaya yönelik programlama modelini WSE 3.0 WCF'de farklıdır. Özel bir belirteci yöneticisi ve bir özel güvenlik belirteci için gerekli olan diğer bileşenlerle nasıl oluşturulacağı hakkında daha fazla ayrıntı için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Özel bir oluşturduysanız `UsernameToken` güvenlik belirteci yöneticisi, WCF, özel bir güvenlik belirteci yöneticisi oluşturmaktan kimlik doğrulaması mantığı belirtmek için daha kolay bir mekanizma sağlar. Daha fazla ayrıntı için [nasıl yapılır: özel kullanıcı adı ve parola Doğrulayıcı kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM kullanan WSE 3.0 Web Hizmetleri kodlanan SOAP iletileri  
 WSE 3 uygulama gibi bir WCF uygulama yapılandırmasında MTOM kodlamasını belirtebilirsiniz. Bu ayar geçirmek için ekleme [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) hizmet için bağlama için. Aşağıdaki kod örneği, nasıl MTOM kodlama de WSE 3.0 WCF'de eşdeğer olan bir hizmet için belirtilen gösterir.  
  
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
  
## <a name="messaging"></a>İleti  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE Mesajlaşma API'si kullanan WSE 3.0 uygulamaları  
 WSE Mesajlaşma API'si istemci ve Web hizmeti arasında iletildiğinde XML doğrudan erişim elde etmek için kullanıldığında, "Düz eski XML" (POX) kullanmak için uygulamayı dönüştürülebilir. POX hakkında daha fazla ayrıntı için bkz. [POX uygulamaları ile birlikte çalışabilirlik](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). WSE Mesajlaşma API'si hakkında daha fazla ayrıntı için bkz. [gönderme ve alma SOAP iletileri kullanarak WSE Mesajlaşma API'si](https://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Taşımalar  
  
### <a name="tcp"></a>TCP  
 Varsayılan olarak, WSE 3.0 istemciler ve TCP aktarımı kullanarak SOAP iletileri gönderen Web Hizmetleri Web Hizmetleri ve WCF istemcileri ile birlikte çalışmadığı. TCP protokolü ve performansı artırmak için kullanılan çerçeve farklılıkları nedeniyle bu uyumsuzluk var. Ancak, bir WCF örnek nasıl uygulanacağını WSE 3.0 ile birlikte çalışan özel bir TCP oturum ayrıntıları. Bu örnek hakkında daha fazla ayrıntı için bkz: [taşıma: WSE 3.0 TCP birlikte çalışabilirlik](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 WCF uygulaması, TCP taşıma kullandığını belirtmek için kullanın [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Özel taşıma  
 Bir kanal uzantısı WSE 3.0 özel taşıma wcf'de eşdeğerdir. Bir kanal uzantısı oluşturma hakkında daha fazla bilgi için bkz: [kanal katmanını genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Programlama Yaşam Döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
