---
title: 'Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 600b9c28d92f9e2b6e4d586b052cc5762d591521
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599067"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma

Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmetleri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında, Microsoft .NET (WVACE) istemcileri için Web Hizmetleri geliştirmeleri 3,0 ile uyumlu değildir.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Bir WCF hizmetinin WVA3,0 istemcileriyle birlikte çalışabilme özelliğini etkinleştirmek için

1. WCF hizmeti için özel bir bağlama tanımlayın.

    WS-Addressing belirtiminin Ağustos 2004 sürümünün ileti kodlama için kullanıldığını belirtmek için, özel bir bağlama oluşturulması gerekir.

    1. [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)Hizmetin yapılandırma dosyasının öğesine bir alt öğesi ekleyin [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) .

    2. Bağlama için bir ad, [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ve özniteliğini ayarlayarak belirtin `name` .

    3. İçin bir alt öğesi ekleyerek WVA3,0 ile uyumlu olan iletilerin güvenliğini sağlamak için kullanılan WS-Security belirtimlerinin bir kimlik doğrulama modu ve sürümünü belirtin [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .

        Kimlik doğrulama modunu ayarlamak için, `authenticationMode` öğesinin özniteliğini ayarlayın [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) . Bir kimlik doğrulama modu, WVA3,0 'de bir anahtar güvenlik onayı ile kabaca eşdeğerdir. Aşağıdaki tablo, WCF 'de kimlik doğrulama modlarını WSE3,0 'de anahtar güvenlik onayları ile eşler.

        |WCF kimlik doğrulama modu|WVA3,0 anahtar güvenlik onayı|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*Ve anahtar güvenlik onayları arasındaki başlıca farklardan biri, `mutualCertificate10Security` `mutualCertificate11Security` Wo 'un soap iletilerini güvenli hale getirmek IÇIN kullandığı WS-Security belirtiminin sürümüdür. İçin `mutualCertificate10Security` WS-security 1,0 kullanılır, ancak IÇIN WS-security 1,1 kullanılır `mutualCertificate11Security` . WCF için WS-Security belirtiminin sürümü `messageSecurityVersion` öğesinin özniteliğinde belirtilir [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .

        SOAP iletilerini güvenli hale getirmek için kullanılan WS-Security belirtiminin sürümünü ayarlamak için, `messageSecurityVersion` özniteliğini ayarlayın [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) . WVA3,0 ile birlikte çalışmak için `messageSecurityVersion` özniteliğinin değerini olarak ayarlayın <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> .

    4. WS-Addressing belirtiminin 2004 Ağustos sürümünün WCF tarafından, bir ekleyerek [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) ve `messageVersion` değerini değerine ayarlayarak belirtin <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> .

        > [!NOTE]
        > SOAP 1,2 kullanırken `messageVersion` özniteliğini olarak ayarlayın <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> .

2. Hizmetin özel bağlamayı kullandığını belirtin.

    1. `binding` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) Öğesinin özniteliğini olarak ayarlayın `customBinding` .

    2. `bindingConfiguration`Öğenin özniteliğini, [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) `name` özel bağlama için öğesinin özniteliğinde belirtilen değere ayarlayın [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `Service.HelloWorldService` wva3,0 istemcileriyle birlikte çalışmak için özel bir bağlama kullandığını belirtir. Özel bağlama, WS-Addressing 2004 Ağustos sürümünün ve WS-Security 1,1 belirtim kümesinin, değiştirilen iletileri kodlamak için kullanıldığını belirtir. İletiler, kimlik doğrulama modu kullanılarak güvenli hale getirilir <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> .

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

- [Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme](../extending/how-to-customize-a-system-provided-binding.md)
