---
title: "Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c93b91123c7622bea125bfa702c53a697b1ac84c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="770dc-102">Nasıl yapılır: WCF Hizmetlerini WSE 3.0 İstemcileriyle Birlikte Çalışmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="770dc-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="770dc-103">Services, Microsoft .NET (WSE) istemciler için Web Hizmetleri geliştirmeleri 3.0 ile hat düzeyinde uyumlu zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="770dc-103"> services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="770dc-104">WSE 3.0 istemcileriyle birlikte çalışmak bir WCF hizmeti etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="770dc-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>  
  
1.  <span data-ttu-id="770dc-105">Özel bağlama için tanımlamak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="770dc-105">Define a custom binding for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
     <span data-ttu-id="770dc-106">WS-adresleme belirtimi Ağustos 2004 sürümü ileti kodlama için kullanıldığını belirtmek için özel bağlama oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="770dc-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>  
  
    1.  <span data-ttu-id="770dc-107">Bir alt öğe ekleyin [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) için [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) hizmetin yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="770dc-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>  
  
    2.  <span data-ttu-id="770dc-108">Ekleyerek bağlama için bir ad belirtin bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) için [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve ayarı `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="770dc-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>  
  
    3.  <span data-ttu-id="770dc-109">Bir kimlik doğrulama modu ve WSE 3.0 ile uyumlu olan bir alt ekleyerek iletileri güvenli hale getirmek için kullanılan WS-güvenlik belirtimleri sürümünü belirtin [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) için [ \<bağlama >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="770dc-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
         <span data-ttu-id="770dc-110">Kimlik doğrulama modu ayarlamak için ayarlayın `authenicationMode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="770dc-110">To set the authentication mode, set the `authenicationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="770dc-111">Bir kimlik doğrulama modu, bir anahtar teslimi güvenlik onaylama işlemi WSE 3.0 kabaca eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="770dc-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="770dc-112">Aşağıdaki tabloda kimlik doğrulama modu eşlemeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] anahtar teslimi güvenlik onaylar WSE 3.0 için.</span><span class="sxs-lookup"><span data-stu-id="770dc-112">The following table maps authentication modes in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to turnkey security assertions in WSE 3.0.</span></span>  
  
        |<span data-ttu-id="770dc-113">WCF kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="770dc-113">WCF Authentication Mode</span></span>|<span data-ttu-id="770dc-114">WSE 3.0 anahtar teslimi güvenlik onaylama işlemi</span><span class="sxs-lookup"><span data-stu-id="770dc-114">WSE 3.0 turnkey security assertion</span></span>|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         <span data-ttu-id="770dc-115">\*Birincil farklarını birini `mutualCertificate10Security` ve `mutualCertificate11Security` anahtar teslimi güvenlik onaylar SOAP iletileri güvenli hale getirmek için WSE kullanan WS-Security belirtimi sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="770dc-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="770dc-116">İçin `mutualCertificate10Security`, WS-Security 1.0 kullanılır, WS-güvenlik 1.1 kullanılırken `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="770dc-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="770dc-117">İçin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], WS-Security belirtimi sürümünü belirtilen `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="770dc-117">For [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="770dc-118">SOAP iletilerine güvenliğini sağlamak için kullanılan WS-Security belirtimi sürümünü ayarlamak için ayarlayın `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="770dc-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="770dc-119">WSE 3.0 ile birlikte çalışmak üzere değerini ayarlamak `messageSecurityVersion` özniteliğini <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="770dc-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>  
  
    4.  <span data-ttu-id="770dc-120">WS-adresleme belirtimi Ağustos 2004 sürümü kullandığı belirtin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ekleyerek bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ve `messageVersion` kendi değerine <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="770dc-120">Specify that the August 2004 version of the WS-Addressing specification is used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="770dc-121">SOAP 1.2 kullanırken ayarlayın `messageVersion` özniteliğini <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="770dc-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>  
  
2.  <span data-ttu-id="770dc-122">Hizmetin özel bağlama kullanacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="770dc-122">Specify that the service uses the custom binding.</span></span>  
  
    1.  <span data-ttu-id="770dc-123">Ayarlama `binding` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesine `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="770dc-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>  
  
    2.  <span data-ttu-id="770dc-124">Ayarlama `bindingConfiguration` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi için belirtilen değer `name` özniteliği [ \<bağlama >](../../../../docs/framework/misc/binding.md) özel bağlama.</span><span class="sxs-lookup"><span data-stu-id="770dc-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="770dc-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="770dc-125">Example</span></span>  
 <span data-ttu-id="770dc-126">Aşağıdaki kod örneğinde belirleyen `Service.HelloWorldService` WSE 3.0 istemcileriyle birlikte çalışmak için özel bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="770dc-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="770dc-127">WS-adresleme Ağustos 2004 sürümü ve belirtim WS güvenliği 1.1 kümesi iletilerin kodlanması için kullanılan özel bağlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="770dc-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="770dc-128">Kullanarak iletileri güvenli <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="770dc-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="770dc-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="770dc-129">See Also</span></span>  
 [<span data-ttu-id="770dc-130">Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="770dc-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
