---
description: 'Daha fazla bilgi edinin: nasıl yapılır: WCF hizmetlerini WCE 3,0 Istemcileriyle birlikte çalışmak üzere yapılandırma'
title: 'Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: d48b24ac7787a9863744ee9b6a4a984cb6b371e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779939"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="79865-103">Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="79865-103">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="79865-104">Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmetleri WS-Addressing belirtim 'in 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında Microsoft .NET (WVACE) istemcileri için Web Hizmetleri geliştirmeleri 3,0 ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="79865-104">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="79865-105">Bir WCF hizmetinin WVA3,0 istemcileriyle birlikte çalışabilme özelliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="79865-105">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="79865-106">WCF hizmeti için özel bir bağlama tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="79865-106">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="79865-107">İleti kodlama için WS-Addressing belirtiminin Ağustos 2004 sürümünün kullanıldığını belirtmek için, özel bir bağlama oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79865-107">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="79865-108">[\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)Hizmetin yapılandırma dosyasının öğesine bir alt öğesi ekleyin [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="79865-108">Add a child [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="79865-109">Bağlama için bir ad, [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ve özniteliğini ayarlayarak belirtin `name` .</span><span class="sxs-lookup"><span data-stu-id="79865-109">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="79865-110">Bir kimlik doğrulama modu ve ' ye bir alt öğesi ekleyerek WVA3,0 ile uyumlu iletileri güvenli hale getirmek için kullanılan WS-Security belirtimlerinin bir sürümünü belirtin [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="79865-110">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="79865-111">Kimlik doğrulama modunu ayarlamak için, `authenticationMode` öğesinin özniteliğini ayarlayın [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="79865-111">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="79865-112">Bir kimlik doğrulama modu, WVA3,0 'de bir anahtar güvenlik onayı ile kabaca eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="79865-112">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="79865-113">Aşağıdaki tablo, WCF 'de kimlik doğrulama modlarını WSE3,0 'de anahtar güvenlik onayları ile eşler.</span><span class="sxs-lookup"><span data-stu-id="79865-113">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="79865-114">WCF kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="79865-114">WCF Authentication Mode</span></span>|<span data-ttu-id="79865-115">WVA3,0 anahtar güvenlik onayı</span><span class="sxs-lookup"><span data-stu-id="79865-115">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="79865-116">\* Ve anahtar güvenlik onayları arasındaki birincil farklardan biri, `mutualCertificate10Security` `mutualCertificate11Security` Wo 'un soap iletilerini güvenli hale getirmek için kullandığı WS-Security belirtiminin sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="79865-116">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="79865-117">İçin `mutualCertificate10Security` WS-Security 1,0 kullanılır, ancak için WS-Security 1,1 kullanılır `mutualCertificate11Security` .</span><span class="sxs-lookup"><span data-stu-id="79865-117">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="79865-118">WCF için WS-Security belirtiminin sürümü `messageSecurityVersion` öğesinin özniteliğinde belirtilir [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="79865-118">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="79865-119">SOAP iletilerini güvenli hale getirmek için kullanılan WS-Security belirtiminin sürümünü ayarlamak için, `messageSecurityVersion` öğesinin özniteliğini ayarlayın [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="79865-119">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="79865-120">WVA3,0 ile birlikte çalışmak için `messageSecurityVersion` özniteliğinin değerini olarak ayarlayın <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> .</span><span class="sxs-lookup"><span data-stu-id="79865-120">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="79865-121">WS-Addressing belirtiminin Ağustos 2004 sürümünün WCF tarafından, bir eklenerek [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) ve değerini değerine ayarlayarak kullanılacağını belirtin `messageVersion` <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="79865-121">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="79865-122">SOAP 1,2 kullanırken `messageVersion` özniteliğini olarak ayarlayın <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="79865-122">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="79865-123">Hizmetin özel bağlamayı kullandığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="79865-123">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="79865-124">`binding` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) Öğesinin özniteliğini olarak ayarlayın `customBinding` .</span><span class="sxs-lookup"><span data-stu-id="79865-124">Set the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="79865-125">`bindingConfiguration`Öğenin özniteliğini, [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) `name` özel bağlama için öğesinin özniteliğinde belirtilen değere ayarlayın [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="79865-125">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="79865-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="79865-126">Example</span></span>

<span data-ttu-id="79865-127">Aşağıdaki kod örneği, `Service.HelloWorldService` wva3,0 istemcileriyle birlikte çalışmak için özel bir bağlama kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="79865-127">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="79865-128">Özel bağlama, değiş tokuş iletilerinin kodlanması için WS-Addressing ve WS-Security 1,1 belirtim kümesinin 2004 sürümünün kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="79865-128">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="79865-129">İletiler, kimlik doğrulama modu kullanılarak güvenli hale getirilir <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> .</span><span class="sxs-lookup"><span data-stu-id="79865-129">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="79865-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79865-130">See also</span></span>

- [<span data-ttu-id="79865-131">Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="79865-131">How to: Customize a System-Provided Binding</span></span>](../extending/how-to-customize-a-system-provided-binding.md)
