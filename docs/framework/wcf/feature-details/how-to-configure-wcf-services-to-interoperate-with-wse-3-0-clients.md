---
title: 'Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: bd9f2bec94ca45f76590f64366428a00edd5d6ea
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141750"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma

Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmetleri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında, Microsoft .NET (WVACE) istemcileri için Web Hizmetleri geliştirmeleri 3,0 ile uyumlu değildir.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Bir WCF hizmetinin WVA3,0 istemcileriyle birlikte çalışabilme özelliğini etkinleştirmek için

1. WCF hizmeti için özel bir bağlama tanımlayın.

    WS-Addressing belirtiminin Ağustos 2004 sürümünün ileti kodlama için kullanıldığını belirtmek için, özel bir bağlama oluşturulması gerekir.

    1. Hizmetin yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) için bir alt [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyin.

    2. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve `name` özniteliğini ayarlayarak [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) ekleyerek bağlama için bir ad belirtin.

    3. [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md)bir alt [\<GÜVENLIK >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ekleyerek wva3,0 ile uyumlu olan iletilerin güvenlIğInI sağlamak Için kullanılan WS-Security belirtimlerinin bir kimlik doğrulaması modunu ve sürümünü belirtin.

        Kimlik doğrulama modunu ayarlamak için [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)`authenticationMode` özniteliğini ayarlayın. Bir kimlik doğrulama modu, WVA3,0 'de bir anahtar güvenlik onayı ile kabaca eşdeğerdir. Aşağıdaki tablo, WCF 'de kimlik doğrulama modlarını WSE3,0 'de anahtar güvenlik onayları ile eşler.

        |WCF kimlik doğrulama modu|WVA3,0 anahtar güvenlik onayı|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        `mutualCertificate10Security` ve `mutualCertificate11Security` anahtar güvenlik onayları arasındaki birincil farklardan biri \*, Wo 'un SOAP iletilerini güvenli hale getirmek için kullandığı WS-Security belirtiminin sürümüdür. WS-Security 1,0 `mutualCertificate10Security`için `mutualCertificate11Security`için WS-Security 1,1 kullanılır. WCF için, WS-Security belirtiminin sürümü [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)`messageSecurityVersion` özniteliğinde belirtilir.

        SOAP iletilerini güvenli hale getirmek için kullanılan WS-Security belirtiminin sürümünü ayarlamak için [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)`messageSecurityVersion` özniteliğini ayarlayın. WVA3,0 ile birlikte çalışmak için `messageSecurityVersion` özniteliğinin değerini <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>olarak ayarlayın.

    4. WS-Addressing belirtiminin 2004 Ağustos sürümünün WCF tarafından [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ekleyerek ve `messageVersion` değerine <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>olarak ayarlandığını belirtin.

        > [!NOTE]
        > SOAP 1,2 kullanırken `messageVersion` özniteliğini <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>olarak ayarlayın.

2. Hizmetin özel bağlamayı kullandığını belirtin.

    1. [\<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesinin `binding` özniteliğini `customBinding`olarak ayarlayın.

    2. [\<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesinin `bindingConfiguration` özniteliğini özel bağlamanın [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) `name` özniteliğinde belirtilen değere ayarlayın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `Service.HelloWorldService` WVA3,0 istemcileriyle birlikte çalışmak için özel bir bağlama kullandığını belirtir. Özel bağlama, WS-Addressing 2004 Ağustos sürümünün ve WS-Security 1,1 belirtim kümesinin, değiştirilen iletileri kodlamak için kullanıldığını belirtir. İletilerin güvenliği <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu kullanılarak yapılır.

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
