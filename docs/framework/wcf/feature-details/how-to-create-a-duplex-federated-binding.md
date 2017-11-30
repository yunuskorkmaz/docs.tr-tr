---
title: "Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a682b84a90e64e0242a3490986cb526c7f028b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="6b9ba-102">Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b9ba-102">How to: Create a Duplex Federated Binding</span></span>
<span data-ttu-id="6b9ba-103"><xref:System.ServiceModel.WSFederationHttpBinding>yalnızca veri birimi ve istek/yanıt iletisi exchange sözleşmeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="6b9ba-104">Çift yönlü ileti exchange sözleşmesi kullanmak için özel bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="6b9ba-105">Aşağıdaki yordamlar bu yapılandırmada, HTTP ve TCP taşımaları için ileti mod güvenliği kullanarak ve TCP taşıma için karma mod güvenliği kullanarak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="6b9ba-106">Tüm 3 bağlamaları gösteren örnek bu konunun sonunda kodudur.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>  
  
 <span data-ttu-id="6b9ba-107">Kodda bağlama de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-107">You can also create the binding in code.</span></span> <span data-ttu-id="6b9ba-108">Bağlama öğeleri yığını oluşturmak için bir açıklaması için bkz: [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="6b9ba-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="6b9ba-109">HTTP ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6b9ba-109">To create a duplex federated custom binding with HTTP</span></span>  
  
1.  <span data-ttu-id="6b9ba-110">İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının düğüm oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>  
  
2.  <span data-ttu-id="6b9ba-111">İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesini oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliği kümesine `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="6b9ba-112">İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesini oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliği kümesine `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="6b9ba-113">İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="6b9ba-114">Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi, boş bir oluşturma [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>  
  
6.  <span data-ttu-id="6b9ba-115">Aşağıdaki [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi, boş bir oluşturma [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>  
  
7.  <span data-ttu-id="6b9ba-116">Aşağıdaki [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi, boş bir oluşturma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="6b9ba-117">TCP ileti güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6b9ba-117">To create a duplex federated custom binding with TCP message security mode</span></span>  
  
1.  <span data-ttu-id="6b9ba-118">İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının düğüm oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="6b9ba-119">İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesini oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliği kümesine `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="6b9ba-120">İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesini oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliği kümesine `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="6b9ba-121">İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="6b9ba-122">Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi, boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="6b9ba-123">Bir çift yönlü oluşturmak için özel bağlama TCP karışık güvenlik modu ile Federasyon</span><span class="sxs-lookup"><span data-stu-id="6b9ba-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>  
  
1.  <span data-ttu-id="6b9ba-124">İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının düğüm oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="6b9ba-125">İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesini oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliği kümesine `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>  
  
3.  <span data-ttu-id="6b9ba-126">İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesini oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliği kümesine `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="6b9ba-127">İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="6b9ba-128">Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi, boş bir oluşturma [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>  
  
6.  <span data-ttu-id="6b9ba-129">Aşağıdaki [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi, boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="6b9ba-130">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="6b9ba-130">Code Sample</span></span>  
  
#### <a name="sample-with-3-bindings"></a><span data-ttu-id="6b9ba-131">Örnek 3 bağlamalarla</span><span class="sxs-lookup"><span data-stu-id="6b9ba-131">Sample with 3 Bindings</span></span>  
  
1.  <span data-ttu-id="6b9ba-132">Yapılandırma dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6b9ba-132">Insert the following code into your configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b9ba-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b9ba-133">Example</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
```
