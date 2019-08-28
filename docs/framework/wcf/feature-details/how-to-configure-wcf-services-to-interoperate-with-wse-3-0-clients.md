---
title: 'Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 0349c9ba76b3f240bf98daa0e095b415bc98a87c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045932"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma

Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmetleri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında, Microsoft .NET (WVACE) istemcileri için Web Hizmetleri geliştirmeleri 3,0 ile uyumlu değildir.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Bir WCF hizmetinin WVA3,0 istemcileriyle birlikte çalışabilme özelliğini etkinleştirmek için

1. WCF hizmeti için özel bir bağlama tanımlayın.

    WS-Addressing belirtiminin Ağustos 2004 sürümünün ileti kodlama için kullanıldığını belirtmek için, özel bir bağlama oluşturulması gerekir.

    1. Hizmetin yapılandırma [dosyasının \<bağlama >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) bir alt [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyin.

    2. `name` CustomBinding > bir [ \<bağlama](../../../../docs/framework/misc/binding.md) [> ekleyip özniteliği ayarlayarak bağlama için bir ad belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

    3. Bağlama > bir alt [ \<güvenlik](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [> ekleyerek, wva3,0 ile uyumlu olan iletilerin güvenliğini sağlamak için kullanılan WS-Security belirtimlerinin bir kimlik doğrulama modunu ve sürümünü belirtin. \<](../../../../docs/framework/misc/binding.md)

        Kimlik doğrulama modunu ayarlamak için `authenticationMode` [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)özniteliğini ayarlayın. Bir kimlik doğrulama modu, WVA3,0 'de bir anahtar güvenlik onayı ile kabaca eşdeğerdir. Aşağıdaki tablo, WCF 'de kimlik doğrulama modlarını WSE3,0 'de anahtar güvenlik onayları ile eşler.

        |WCF kimlik doğrulama modu|WVA3,0 anahtar güvenlik onayı|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*`mutualCertificate10Security` Ve`mutualCertificate11Security` anahtar güvenlik onayları arasındaki başlıca farklardan biri, Wo 'un soap iletilerini güvenli hale getirmek için kullandığı WS-Security belirtiminin sürümüdür. İçin `mutualCertificate10Security`WS-Security 1,0 kullanılır, ancak için `mutualCertificate11Security`WS-Security 1,1 kullanılır. WCF için, WS-Security belirtiminin sürümü `messageSecurityVersion` [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)özniteliğinde belirtilir.

        SOAP iletilerini güvenli hale getirmek için kullanılan WS-Security belirtiminin sürümünü ayarlamak için `messageSecurityVersion` [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)özniteliğini ayarlayın. Wva3,0 ile birlikte çalışmak için `messageSecurityVersion` özniteliğinin değerini olarak <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>ayarlayın.

    4. WS-Addressing belirtiminin 2004 Ağustos sürümünün WCF tarafından bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ekleyerek ve `messageVersion` değerini değerine <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>ayarlayarak belirtin.

        > [!NOTE]
        > SOAP 1,2 kullanırken `messageVersion` özniteliğini olarak <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>ayarlayın.

2. Hizmetin özel bağlamayı kullandığını belirtin.

    1. Endpoint > öğesinin `binding` özniteliğini olarak`customBinding`ayarlayın. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)

    2. Endpoint > `bindingConfiguration` [öğesinin özniteliğini özel bağlama için bağlama > özniteliğinde \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) belirtilen [ \<değere ayarlayın](../../../../docs/framework/misc/binding.md) `name` .

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `Service.HelloWorldService` wva3,0 istemcileriyle birlikte çalışmak için özel bir bağlama kullandığını belirtir. Özel bağlama, WS-Addressing 2004 Ağustos sürümünün ve WS-Security 1,1 belirtim kümesinin, değiştirilen iletileri kodlamak için kullanıldığını belirtir. İletiler, <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu kullanılarak güvenli hale getirilir.

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

- [Nasıl yapılır: Sistem tarafından sağlanmış bağlamayı özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
