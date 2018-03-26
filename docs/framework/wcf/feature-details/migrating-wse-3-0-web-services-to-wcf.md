---
title: WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7e7187eb6ed444ba2c28aa301ce4b3b16129030
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web Hizmetlerini WCF'ye Taşıma
Geçirme WSE 3.0 Web hizmetlerini yararları [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Gelişmiş performans ve ek taşımalar, ek güvenlik senaryoları ve WS - desteği dahil * belirtimleri. WSE 3.0 geçirilmiş bir Web hizmeti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en fazla 200-% 400 performans iyileştirmesi yaşayabilirsiniz. Tarafından desteklenen aktarmalar hakkında daha fazla bilgi için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Tarafından desteklenen senaryolarla listesi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [ortak güvenlik senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Tarafından desteklenen belirtimleri listesi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Aşağıdaki bölümler, belirli bir özelliği olan bir WSE 3.0 Web hizmetine geçirme konusunda rehberlik sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="general"></a>Genel  
 WSE 3.0 ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hat düzeyinde birlikte çalışabilirlik ve terminolojisi ortak bir dizi uygulamaları içerir. WSE 3.0 ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalardır hat WS-kümesini temel alan düzeyinde birlikte çalışabilir * belirtimlerini her ikisi de destekler. WSE 3.0 olduğunda veya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama geliştirilen terminoloji, anahtar teslimi güvenlik onaylar WSE ve kimlik doğrulama modları adları gibi ortak bir dizi yoktur.  
  
 Vardır, ancak birçok benzer yönü arasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET veya modellerini programlama WSE 3.0, bunlar farklı. Hakkındaki ayrıntılar için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programlama modeli, bkz: [temel programlama yaşam döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  WSE Web hizmeti için WCF geçirmek için [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı, bir istemci oluşturmak için kullanılabilir. Başlangıç olarak kullanılan sınıflar için bir WCF hizmeti çok noktası ve istemci ancak arabirimlerini içerir. Oluşturulan arabirimine sahip <xref:System.ServiceModel.OperationContractAttribute> sözleşmeyle üyelerine uygulanan öznitelik <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliğini `*`. WSE istemci ile bu ayar bir Web hizmeti aradığında, aşağıdaki özel durum oluşur: **Web.Services3.ResponseProcessingException: WSE910: bir yanıt iletisi işlenmesi sırasında bir hata oluştu ve iç hata bulabilirsiniz özel durum**. Bu durumu iyileştirmek için ayarlanmış <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliği <xref:System.ServiceModel.OperationContractAttribute> özniteliği olmayan bir`null` gibi değerini `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Güvenlik  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Bir ilke dosyası kullanılarak güvenlik altına WSE 3.0 Web Hizmetleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bu mekanizma WSE 3.0 ilke dosyasına benzer ve Hizmetleri bir hizmeti güvenli hale getirmek için bir yapılandırma dosyası kullanabilirsiniz. WSE bir ilke dosyası kullanarak bir Web hizmeti güvenli hale getirirken 3.0 bir anahtar teslimi güvenlik onaylama işlemi ya da bir özel ilke onaylama kullanın. Anahtar teslimi güvenlik onaylar eşleme yakından kimlik doğrulama modu için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik bağlama öğesi. Değil yalnızca [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimlik doğrulama modları ve WSE 3.0 anahtar teslimi güvenlik onaylar adlı aynı veya benzer şekilde, bunlar aynı kimlik bilgisi türlerini kullanarak iletileri güvenli. Örneğin, `usernameForCertificate` anahtar teslimi güvenlik onaylama işlemi WSE 3.0 eşlendiğini `UsernameForCertificate` kimlik doğrulama modunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Aşağıdaki kod örnekleri kullanan en az bir ilke nasıl göstermek `usernameForCertificate` anahtar teslimi güvenlik onaylama işlemi WSE 3.0 eşlendiğini bir `UsernameForCertificate` kimlik doğrulama modunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel bağlama içinde.  
  
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
  
 Bir ilke dosyası içinde belirtilen bir WSE 3.0 Web hizmeti güvenlik ayarlarını geçirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], özel bağlama yapılandırma dosyasında oluşturulmalı ve anahtar teslimi güvenlik onaylama işlemi, eşdeğer bir kimlik doğrulama modu için ayarlamanız gerekir. Ayrıca, özel bağlama Ağustos 2004 kullanacak şekilde yapılandırılması gerekir WSE 3.0 istemciler hizmeti ile iletişim kurduğunda WS adresleme belirtimi. Zaman geçirilen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet WSE 3.0 istemcileriyle iletişim gerektirmez ve yalnızca güvenlik eşlik korumalıdır, kullanmayı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel oluşturmak yerine uygun güvenlik ayarları ile sistem tanımlı bağlamalar bağlama.  
  
 Aşağıdaki tabloda WSE 3.0 ilke dosyası ve bağlama özel eşdeğeri arasında eşleme listeler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|WSE 3.0 anahtar teslimi güvenlik onaylama işlemi|WCF özel bağlama yapılandırma|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF'de özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Uygulama kodu kullanılarak güvenlik altına WSE 3.0 Web Hizmetleri  
 Olup olmadığını WSE 3.0 veya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olan kullanıldığında, güvenlik gereksinimlerini uygulama kodundaki yerine yapılandırmasında belirtilebilir. WSE 3. 0'da, bu türeyen bir sınıf oluşturarak gerçekleştirilir `Policy` sınıfı ve çağırarak gereksinimlerine göre ekleyerek `Add` yöntemi. Kodda güvenlik gereksinimlerini belirtme hakkında daha fazla ayrıntı için bkz: [nasıl yapılır: bir ilke dosyasını güvenli bir Web hizmeti olmadan kullanarak](http://go.microsoft.com/fwlink/?LinkId=73747). İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], kodda güvenlik gereksinimlerini belirtme, bir örneğini oluşturmak için <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve bir örnek ekler bir <xref:System.ServiceModel.Channels.SecurityBindingElement> için <xref:System.ServiceModel.Channels.BindingElementCollection>. Statik kimlik doğrulama modu yardımcı yöntemlerinden birini kullanarak güvenlik onaylama işlemi gereksinimleri ayarlayın <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Kod kullanarak güvenlik gereksinimlerini belirtme hakkında daha fazla ayrıntı için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) ve [nasıl yapılır: için SecurityBindingElement oluşturma bir Belirtilen kimlik doğrulama modu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 özel ilkesini onaylama  
 WSE 3.0 özel ilke onaylamalarını iki tür vardır: da güvenli bir SOAP iletisi ve, bir SOAP iletisi güvenli değil. SOAP iletilerine güvenli ilke onaylamalarını WSE 3.0 türetilen `SecurityPolicyAssertion` sınıfı ve kavramsal eşdeğer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olan <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.  
  
 Dikkat edilecek önemli bir WSE 3.0 anahtar teslimi güvenlik onaylar alt kümesi olan noktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimlik doğrulama modu. Bir özel ilke onaylama WSE 3.0 oluşturduysanız, eşdeğer bir olabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimlik doğrulama modu. Örneğin, WSE 3.0 eşdeğeridir bir CertificateOverTransport güvenlik onaylama işlemi sağlamaz `UsernameOverTransport` anahtar teslimi güvenlik onaylama işlemi, ancak istemci kimlik doğrulama amacıyla bir X.509 sertifikası kullanır. Bu senaryo için kendi özel ilke onaylama tanımladıysanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geçişi basitleştirir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bu senaryo için bir kimlik doğrulama modu, statik kimlik doğrulama modunu yapılandırmak için yardımcı yöntemler yararlanabilir şekilde tanımlayan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Olmadığında bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP iletileri güvenli hale getiren bir özel ilke onaylama eşdeğer olan kimlik doğrulama modu türetilen bir sınıftan <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sınıfları ve eşdeğer bağlama belirtme öğesi. Daha fazla ayrıntı için bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Bir SOAP iletisi güvenli olmayan bir özel ilke onaylama dönüştürmek için bkz: [filtreleme](../../../../docs/framework/wcf/feature-details/filtering.md) ve örnek [özel ileti kesici](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 özel güvenlik belirteci  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Özel bir belirteç oluşturmak için programlama modelini WSE 3.0 farklı. WSE içinde özel belirteç oluşturma hakkında daha fazla bilgi için bkz: [oluşturma özel güvenlik belirteçleri](http://go.microsoft.com/fwlink/?LinkID=73750). İçinde özel belirteç oluşturma hakkında daha fazla ayrıntı için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 özel belirteci yöneticisi  
 Özel bir belirteci yöneticisi oluşturmak için programlama modelini farklıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 daha. Özel bir belirteci yöneticisi ve bir özel güvenlik belirteci için gerekli olan diğer bileşenlerle nasıl oluşturulacağı hakkında daha fazla ayrıntı için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Özel bir oluşturduysanız `UsernameToken` güvenlik belirteci yöneticisi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel bir güvenlik belirteci yöneticisi oluşturma daha kimlik doğrulaması mantığı belirtmek için daha kolay bir mekanizma sağlar. Daha fazla ayrıntı için bkz: [nasıl yapılır: özel kullanıcı adı ve parola Doğrulayıcı kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>SOAP iletilerine MTOM kullanan WSE 3.0 Web Hizmetleri kodlanmış  
 WSE 3 uygulama gibi bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama yapılandırmasında kodlama MTOM iletisi belirtebilirsiniz. Bu ayar geçirmek için add [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) hizmet için bağlama için. Aşağıdaki kod örneğinde nasıl MTOM kodlama WSE 3.0 içinde de eşdeğer bir gruba bir hizmet için belirtilen gösterilmektedir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
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
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>İleti WSE API kullanan WSE 3.0 uygulamaları  
 İleti WSE API İstemci ve Web hizmeti arasında iletişim XML doğrudan erişmek için kullanıldığında, uygulama "Düz eski XML" (POX) kullanmak için dönüştürülebilir. POX hakkında daha fazla ayrıntı için bkz: [POX uygulamaları ile birlikte çalışabilirlik](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). İleti WSE API hakkında daha fazla ayrıntı için [gönderme ve alma SOAP iletileri kullanarak WSE Mesajlaşma API](http://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Taşımalar  
  
### <a name="tcp"></a>TCP  
 Varsayılan olarak, WSE 3.0 istemcileri ve TCP taşıma kullanarak SOAP iletileri gönder Web Hizmetleri ile birlikte çalışmak değil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler ve Web Hizmetleri. TCP protokolü ve performansı artırmak için kullanılan çerçeveleme farklılıkları nedeniyle bu uyumsuzluk var. Ancak, bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnek ayrıntıları WSE 3.0 ile birlikte çalışır özel bir TCP oturumu gerçekleştirme. Bu örnek hakkında daha fazla ayrıntı için bkz: [taşıma: WSE 3.0 TCP birlikte çalışabilirlik](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Belirtmek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamanın kullandığı TCP taşıma, kullanın [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Özel taşıma  
 Bir WSE 3.0 özel taşıma denk [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir kanal uzantısıdır. Bir kanal uzantısı oluşturma hakkında daha fazla bilgi için bkz: [kanal katmanını genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Programlama Yaşam Döngüsü](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
