---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 510faa0b1d791b1d164c55e9fa32daafa559d56c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696216"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="22221-102">Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="22221-102">How to: Create a Duplex Federated Binding</span></span>
<span data-ttu-id="22221-103"><xref:System.ServiceModel.WSFederationHttpBinding> yalnızca veri birimi ve istek/yanıt iletisi exchange sözleşmeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="22221-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="22221-104">Çift yönlü ileti exchange anlaşması kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="22221-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="22221-105">Aşağıdaki yordamlar yapılandırmasında, HTTP ve TCP taşımalar için ileti modu güvenliği ve karma mod güvenliği için TCP taşıması kullanarak bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22221-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="22221-106">Tüm 3 bağlamaları gösteren örnek kodlara, bu konunun sonunda ' dir.</span><span class="sxs-lookup"><span data-stu-id="22221-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>  
  
 <span data-ttu-id="22221-107">Ayrıca, kod içinde bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22221-107">You can also create the binding in code.</span></span> <span data-ttu-id="22221-108">Oluşturmak için bağlama öğeleri yığın açıklaması için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="22221-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="22221-109">HTTP ile özel çift yönlü federe bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="22221-109">To create a duplex federated custom binding with HTTP</span></span>  
  
1. <span data-ttu-id="22221-110">İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası düğümü oluşturmak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>  
  
2. <span data-ttu-id="22221-111">İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliğini `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="22221-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>  
  
3. <span data-ttu-id="22221-112">İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliğini `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="22221-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4. <span data-ttu-id="22221-113">İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="22221-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5. <span data-ttu-id="22221-114">Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi boş bir oluşturma [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>  
  
6. <span data-ttu-id="22221-115">Aşağıdaki [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi boş bir oluşturma [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>  
  
7. <span data-ttu-id="22221-116">Aşağıdaki [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi boş bir oluşturma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="22221-117">TCP ileti güvenlik modunu ile özel çift yönlü federe bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="22221-117">To create a duplex federated custom binding with TCP message security mode</span></span>  
  
1. <span data-ttu-id="22221-118">İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası düğümü oluşturmak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2. <span data-ttu-id="22221-119">İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliğini `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="22221-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>  
  
3. <span data-ttu-id="22221-120">İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliğini `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="22221-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4. <span data-ttu-id="22221-121">İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="22221-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5. <span data-ttu-id="22221-122">Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="22221-123">Bir çift yönlü oluşturmak için özel bir bağlama TCP karma güvenlik modu ile Federasyon</span><span class="sxs-lookup"><span data-stu-id="22221-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>  
  
1. <span data-ttu-id="22221-124">İçinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası düğümü oluşturmak bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2. <span data-ttu-id="22221-125">İçinde [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturmak bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğeyle `name` özniteliğini `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="22221-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>  
  
3. <span data-ttu-id="22221-126">İçinde [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturmak bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğeyle `authenticationMode` özniteliğini `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="22221-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4. <span data-ttu-id="22221-127">İçinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturmak bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğeyle `authenticationMode` özniteliğini `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="22221-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5. <span data-ttu-id="22221-128">Aşağıdaki [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi boş bir oluşturma [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>  
  
6. <span data-ttu-id="22221-129">Aşağıdaki [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi boş bir oluşturma [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="22221-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="22221-130">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="22221-130">Code Sample</span></span>  
  
#### <a name="sample-with-3-bindings"></a><span data-ttu-id="22221-131">Örnek 3 bağlamaları ile</span><span class="sxs-lookup"><span data-stu-id="22221-131">Sample with 3 Bindings</span></span>  
  
1. <span data-ttu-id="22221-132">Yapılandırma dosyanıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="22221-132">Insert the following code into your configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22221-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="22221-133">Example</span></span>  
  
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
