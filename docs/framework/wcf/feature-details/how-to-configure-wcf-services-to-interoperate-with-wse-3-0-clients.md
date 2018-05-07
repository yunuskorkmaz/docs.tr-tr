---
title: 'Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 174ecd279f9380136532ce0d5105b7a71b6d88da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma
WCF hizmetleri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırıldıklarında Windows Communication Foundation (WCF) hizmetlerini hat düzeyinde Web Hizmetleri geliştirmeleri 3.0 ile Microsoft .NET (WSE) istemciler için uyumludur.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>WSE 3.0 istemcileriyle birlikte çalışmak bir WCF hizmeti etkinleştirmek için  
  
1.  WCF hizmeti için özel bir bağlama tanımlayın.  
  
     WS-adresleme belirtimi Ağustos 2004 sürümü ileti kodlama için kullanıldığını belirtmek için özel bağlama oluşturulması gerekir.  
  
    1.  Bir alt öğe ekleyin [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) için [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) hizmetin yapılandırma dosyası.  
  
    2.  Ekleyerek bağlama için bir ad belirtin bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) için [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve ayarı `name` özniteliği.  
  
    3.  Bir kimlik doğrulama modu ve WSE 3.0 ile uyumlu olan bir alt ekleyerek iletileri güvenli hale getirmek için kullanılan WS-güvenlik belirtimleri sürümünü belirtin [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) için [ \<bağlama >](../../../../docs/framework/misc/binding.md).  
  
         Kimlik doğrulama modu ayarlamak için ayarlayın `authenicationMode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Bir kimlik doğrulama modu, bir anahtar teslimi güvenlik onaylama işlemi WSE 3.0 kabaca eşdeğerdir. Aşağıdaki tabloda wcf'de kimlik doğrulama modları anahtar teslimi güvenlik onaylar WSE 3.0 eşler.  
  
        |WCF kimlik doğrulama modu|WSE 3.0 anahtar teslimi güvenlik onaylama işlemi|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* Birincil farklarını birini `mutualCertificate10Security` ve `mutualCertificate11Security` anahtar teslimi güvenlik onaylar SOAP iletileri güvenli hale getirmek için WSE kullanan WS-Security belirtimi sürümüdür. İçin `mutualCertificate10Security`, WS-Security 1.0 kullanılır, WS-güvenlik 1.1 kullanılırken `mutualCertificate11Security`. WCF için WS-Security belirtimi sürümünü belirtilen `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         SOAP iletilerine güvenliğini sağlamak için kullanılan WS-Security belirtimi sürümünü ayarlamak için ayarlayın `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). WSE 3.0 ile birlikte çalışmak üzere değerini ayarlamak `messageSecurityVersion` özniteliğini <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  WS-adresleme belirtimi Ağustos 2004 sürümü ekleyerek WCF tarafından kullanıldığını belirtmek bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ve `messageVersion` kendi değerine <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  SOAP 1.2 kullanırken ayarlayın `messageVersion` özniteliğini <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Hizmetin özel bağlama kullanacağını belirtin.  
  
    1.  Ayarlama `binding` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesine `customBinding`.  
  
    2.  Ayarlama `bindingConfiguration` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi için belirtilen değer `name` özniteliği [ \<bağlama >](../../../../docs/framework/misc/binding.md) özel bağlama.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde belirleyen `Service.HelloWorldService` WSE 3.0 istemcileriyle birlikte çalışmak için özel bağlama kullanır. WS-adresleme Ağustos 2004 sürümü ve belirtim WS güvenliği 1.1 kümesi iletilerin kodlanması için kullanılan özel bağlama belirtir. Kullanarak iletileri güvenli <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        behaviorConfiguration="ServiceBehavior"   
        name="Service.HelloWorldService">  
        <endpoint binding="customBinding" address=""  
          bindingConfiguration="ServiceBinding"  
          contract="Service.IHelloWorld"></endpoint>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="ServiceBinding">  
          <security authenticationMode="AnonymousForCertificate"  
                  messageProtectionOrder="SignBeforeEncrypt"  
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"  
                  requireDerivedKeys="false">  
          </security>  
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">  
        <serviceCredentials>  
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>  
        </serviceCredentials>  
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
