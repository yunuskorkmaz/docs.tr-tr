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
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="d3cb6-102">Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d3cb6-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="d3cb6-103">Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmetleri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında, Microsoft .NET (WVACE) istemcileri için Web Hizmetleri geliştirmeleri 3,0 ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="d3cb6-104">Bir WCF hizmetinin WVA3,0 istemcileriyle birlikte çalışabilme özelliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d3cb6-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="d3cb6-105">WCF hizmeti için özel bir bağlama tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="d3cb6-106">WS-Addressing belirtiminin Ağustos 2004 sürümünün ileti kodlama için kullanıldığını belirtmek için, özel bir bağlama oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="d3cb6-107">Hizmetin yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) için bir alt [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="d3cb6-108">[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve `name` özniteliğini ayarlayarak [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) ekleyerek bağlama için bir ad belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-108">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="d3cb6-109">[\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md)bir alt [\<GÜVENLIK >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ekleyerek wva3,0 ile uyumlu olan iletilerin güvenlIğInI sağlamak Için kullanılan WS-Security belirtimlerinin bir kimlik doğrulaması modunu ve sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="d3cb6-110">Kimlik doğrulama modunu ayarlamak için [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)`authenticationMode` özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="d3cb6-111">Bir kimlik doğrulama modu, WVA3,0 'de bir anahtar güvenlik onayı ile kabaca eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="d3cb6-112">Aşağıdaki tablo, WCF 'de kimlik doğrulama modlarını WSE3,0 'de anahtar güvenlik onayları ile eşler.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="d3cb6-113">WCF kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="d3cb6-113">WCF Authentication Mode</span></span>|<span data-ttu-id="d3cb6-114">WVA3,0 anahtar güvenlik onayı</span><span class="sxs-lookup"><span data-stu-id="d3cb6-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="d3cb6-115">`mutualCertificate10Security` ve `mutualCertificate11Security` anahtar güvenlik onayları arasındaki birincil farklardan biri \*, Wo 'un SOAP iletilerini güvenli hale getirmek için kullandığı WS-Security belirtiminin sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="d3cb6-116">WS-Security 1,0 `mutualCertificate10Security`için `mutualCertificate11Security`için WS-Security 1,1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="d3cb6-117">WCF için, WS-Security belirtiminin sürümü [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)`messageSecurityVersion` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="d3cb6-118">SOAP iletilerini güvenli hale getirmek için kullanılan WS-Security belirtiminin sürümünü ayarlamak için [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)`messageSecurityVersion` özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="d3cb6-119">WVA3,0 ile birlikte çalışmak için `messageSecurityVersion` özniteliğinin değerini <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="d3cb6-120">WS-Addressing belirtiminin 2004 Ağustos sürümünün WCF tarafından [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ekleyerek ve `messageVersion` değerine <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>olarak ayarlandığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="d3cb6-121">SOAP 1,2 kullanırken `messageVersion` özniteliğini <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="d3cb6-122">Hizmetin özel bağlamayı kullandığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="d3cb6-123">[\<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesinin `binding` özniteliğini `customBinding`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="d3cb6-124">[\<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesinin `bindingConfiguration` özniteliğini özel bağlamanın [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) `name` özniteliğinde belirtilen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="d3cb6-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3cb6-125">Example</span></span>

<span data-ttu-id="d3cb6-126">Aşağıdaki kod örneği, `Service.HelloWorldService` WVA3,0 istemcileriyle birlikte çalışmak için özel bir bağlama kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="d3cb6-127">Özel bağlama, WS-Addressing 2004 Ağustos sürümünün ve WS-Security 1,1 belirtim kümesinin, değiştirilen iletileri kodlamak için kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="d3cb6-128">İletilerin güvenliği <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d3cb6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3cb6-129">See also</span></span>

- [<span data-ttu-id="d3cb6-130">Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3cb6-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
