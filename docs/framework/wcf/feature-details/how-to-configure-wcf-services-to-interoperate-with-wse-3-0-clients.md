---
title: 'Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 8f4407f66095f97a213d6cd987b4bd9a3ed340fa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303901"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma
Windows Communication Foundation (WCF) hizmetlerini WCF hizmetleri belirtiminin WS-Addressing Ağustos 2004 sürümü kullanmak üzere yapılandırılmış hat düzeyinde (WSE) Microsoft .NET istemcileri için Web Hizmetleri iyileştirmeleri 3.0 uyumlu olur.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>WSE 3.0 istemcileriyle birlikte çalışmak bir WCF hizmetini etkinleştirmek için  
  
1. WCF hizmeti için özel bir bağlama tanımlar.  
  
     Belirtiminin WS-Addressing Ağustos 2004 sürümü ileti kodlama için kullanıldığını belirtmek için özel bir bağlama yeniden oluşturulması gerekir.  
  
    1.  Bir alt öğe Ekle [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) için [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) hizmetin yapılandırma dosyası.  
  
    2.  Ekleyerek bağlama için bir ad belirtin. bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) için [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve ayarı `name` özniteliği.  
  
    3.  Bir kimlik doğrulama modu ve bir alt ekleyerek WSE 3.0 ile uyumlu olan iletileri güvenli hale getirmek için kullanılan WS-güvenlik belirtimleri sürümünü belirtin [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) için [ \<bağlama >](../../../../docs/framework/misc/binding.md).  
  
         Kimlik doğrulama modu ayarlamak için ayarlayın `authenicationMode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Bir kimlik doğrulama modu, bir kullanıma hazır güvenlik onaylama işlemi WSE 3.0 kabaca eşdeğerdir. Aşağıdaki tabloda, kullanıma hazır güvenlik onaylar WSE 3.0 wcf'de kimlik doğrulama modları eşlenir.  
  
        |WCF kimlik doğrulama modu|WSE 3.0 kullanıma hazır güvenlik onaylama işlemi|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* Arasındaki temel farklar birini `mutualCertificate10Security` ve `mutualCertificate11Security` kullanıma hazır güvenlik onaylar SOAP iletileri güvenli hale getirmek için WSE kullanan WS-Security belirtimi sürümüdür. İçin `mutualCertificate10Security`, WS-güvenlik 1.0 kullanılır, WS-güvenlik 1.1 kullanılırken `mutualCertificate11Security`. WCF için WS-güvenlik belirtiminin sürümünü belirtilen `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         SOAP iletilerini korumak için kullanılan WS-Security belirtimi ayarlamak üzere ayarlanmış `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). WSE 3.0 ile çalışmak için değerini ayarlamak `messageSecurityVersion` özniteliğini <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  WS-Addressing belirtimi Ağustos 2004 sürümü ekleyerek WCF tarafından kullanıldığını belirtmek bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ayarlayıp `messageVersion` değerine için <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  SOAP 1.2 kullanırken ayarlayın `messageVersion` özniteliğini <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2. Hizmetin özel bağlama kullanacağını belirtin.  
  
    1.  Ayarlama `binding` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesine `customBinding`.  
  
    2.  Ayarlama `bindingConfiguration` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) içinde belirtilen değerle bir öğeye `name` özniteliği [ \<bağlama >](../../../../docs/framework/misc/binding.md) özel bağlama.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği belirten `Service.HelloWorldService` WSE 3.0 istemcileriyle birlikte çalışmak için özel bir bağlama kullanır. WS-Addressing Ağustos 2004 sürümü ve WS-güvenlik 1.1 kümesi belirtimleri iletilerin kodlamak için kullanılan özel bağlama belirtir. Kullanarak iletileri güvenli <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
