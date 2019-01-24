---
title: 'Nasıl yapılır: WCF hizmetlerini WSE 3.0 istemcileriyle birlikte çalışmak için yapılandırma'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: d42e2d4c0bf4c708f2dbb27d14d1adddc3fead41
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635799"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="0d8fc-102">Nasıl yapılır: WCF hizmetlerini WSE 3.0 istemcileriyle birlikte çalışmak için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0d8fc-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>
<span data-ttu-id="0d8fc-103">Windows Communication Foundation (WCF) hizmetlerini WCF hizmetleri belirtiminin WS-Addressing Ağustos 2004 sürümü kullanmak üzere yapılandırılmış hat düzeyinde (WSE) Microsoft .NET istemcileri için Web Hizmetleri iyileştirmeleri 3.0 uyumlu olur.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="0d8fc-104">WSE 3.0 istemcileriyle birlikte çalışmak bir WCF hizmetini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="0d8fc-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>  
  
1.  <span data-ttu-id="0d8fc-105">WCF hizmeti için özel bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-105">Define a custom binding for the WCF service.</span></span>  
  
     <span data-ttu-id="0d8fc-106">Belirtiminin WS-Addressing Ağustos 2004 sürümü ileti kodlama için kullanıldığını belirtmek için özel bir bağlama yeniden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>  
  
    1.  <span data-ttu-id="0d8fc-107">Bir alt öğe Ekle [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) için [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) hizmetin yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>  
  
    2.  <span data-ttu-id="0d8fc-108">Ekleyerek bağlama için bir ad belirtin. bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) için [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve ayarı `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>  
  
    3.  <span data-ttu-id="0d8fc-109">Bir kimlik doğrulama modu ve bir alt ekleyerek WSE 3.0 ile uyumlu olan iletileri güvenli hale getirmek için kullanılan WS-güvenlik belirtimleri sürümünü belirtin [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) için [ \<bağlama >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="0d8fc-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
         <span data-ttu-id="0d8fc-110">Kimlik doğrulama modu ayarlamak için ayarlayın `authenicationMode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0d8fc-110">To set the authentication mode, set the `authenicationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="0d8fc-111">Bir kimlik doğrulama modu, bir kullanıma hazır güvenlik onaylama işlemi WSE 3.0 kabaca eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="0d8fc-112">Aşağıdaki tabloda, kullanıma hazır güvenlik onaylar WSE 3.0 wcf'de kimlik doğrulama modları eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>  
  
        |<span data-ttu-id="0d8fc-113">WCF kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="0d8fc-113">WCF Authentication Mode</span></span>|<span data-ttu-id="0d8fc-114">WSE 3.0 kullanıma hazır güvenlik onaylama işlemi</span><span class="sxs-lookup"><span data-stu-id="0d8fc-114">WSE 3.0 turnkey security assertion</span></span>|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         <span data-ttu-id="0d8fc-115">\* Arasındaki temel farklar birini `mutualCertificate10Security` ve `mutualCertificate11Security` kullanıma hazır güvenlik onaylar SOAP iletileri güvenli hale getirmek için WSE kullanan WS-Security belirtimi sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="0d8fc-116">İçin `mutualCertificate10Security`, WS-güvenlik 1.0 kullanılır, WS-güvenlik 1.1 kullanılırken `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="0d8fc-117">WCF için WS-güvenlik belirtiminin sürümünü belirtilen `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0d8fc-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="0d8fc-118">SOAP iletilerini korumak için kullanılan WS-Security belirtimi ayarlamak üzere ayarlanmış `messageSecurityVersion` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0d8fc-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="0d8fc-119">WSE 3.0 ile çalışmak için değerini ayarlamak `messageSecurityVersion` özniteliğini <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>  
  
    4.  <span data-ttu-id="0d8fc-120">WS-Addressing belirtimi Ağustos 2004 sürümü ekleyerek WCF tarafından kullanıldığını belirtmek bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) ayarlayıp `messageVersion` değerine için <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0d8fc-121">SOAP 1.2 kullanırken ayarlayın `messageVersion` özniteliğini <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>  
  
2.  <span data-ttu-id="0d8fc-122">Hizmetin özel bağlama kullanacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-122">Specify that the service uses the custom binding.</span></span>  
  
    1.  <span data-ttu-id="0d8fc-123">Ayarlama `binding` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesine `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>  
  
    2.  <span data-ttu-id="0d8fc-124">Ayarlama `bindingConfiguration` özniteliği [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) içinde belirtilen değerle bir öğeye `name` özniteliği [ \<bağlama >](../../../../docs/framework/misc/binding.md) özel bağlama.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d8fc-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d8fc-125">Example</span></span>  
 <span data-ttu-id="0d8fc-126">Aşağıdaki kod örneği belirten `Service.HelloWorldService` WSE 3.0 istemcileriyle birlikte çalışmak için özel bir bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="0d8fc-127">WS-Addressing Ağustos 2004 sürümü ve WS-güvenlik 1.1 kümesi belirtimleri iletilerin kodlamak için kullanılan özel bağlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="0d8fc-128">Kullanarak iletileri güvenli <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d8fc-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d8fc-129">See also</span></span>
- [<span data-ttu-id="0d8fc-130">Nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0d8fc-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
