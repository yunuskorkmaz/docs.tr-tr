---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141722"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="fdd10-102">Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdd10-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="fdd10-103"><xref:System.ServiceModel.WSFederationHttpBinding> yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="fdd10-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="fdd10-104">Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd10-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="fdd10-105">Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fdd10-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="fdd10-106">Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fdd10-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="fdd10-107">Ayrıca, koddaki bağlamayı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd10-107">You can also create the binding in code.</span></span> <span data-ttu-id="fdd10-108">Oluşturulacak bağlama öğeleri yığınının bir açıklaması için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="fdd10-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="fdd10-109">HTTP ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fdd10-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="fdd10-110">Yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) düğümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="fdd10-111">[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesinin içinde `name` özniteliği `FederationDuplexHttpMessageSecurityBinding`olarak ayarlanmış bir [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="fdd10-112">[\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin içinde `authenticationMode` özniteliği `SecureConversation`olarak ayarlanmış bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="fdd10-113">[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesinin içinde `authenticationMode` özniteliği `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`olarak ayarlanmış bir [\<securebir Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="fdd10-114">[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini izleyerek boş bir [\<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="fdd10-115">[\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesini izleyerek boş bir [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="fdd10-116">[\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesini izleyerek boş bir [\<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="fdd10-117">Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fdd10-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="fdd10-118">Yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) düğümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="fdd10-119">[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesinin içinde `name` özniteliği `FederationDuplexTcpMessageSecurityBinding`olarak ayarlanmış bir [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="fdd10-120">[\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin içinde `authenticationMode` özniteliği `SecureConversation`olarak ayarlanmış bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="fdd10-121">[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesinin içinde `authenticationMode` özniteliği `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`olarak ayarlanmış bir [\<securebir Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="fdd10-122">[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini izleyerek boş bir [\<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="fdd10-123">TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fdd10-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="fdd10-124">Yapılandırma dosyasının [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) düğümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="fdd10-125">[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) öğesinin içinde `name` özniteliği `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`olarak ayarlanmış bir [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="fdd10-126">[\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin içinde `authenticationMode` özniteliği `SecureConversation`olarak ayarlanmış bir [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="fdd10-127">[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesinin içinde `authenticationMode` özniteliği `IssuedTokenForCertificate` veya `IssuedTokenForSslNegotiated`olarak ayarlanmış bir [\<securebir Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="fdd10-128">[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesini izleyerek boş bir [\<sslstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="fdd10-129">[\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesini izleyerek boş bir [\<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fdd10-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fdd10-130">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="fdd10-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="fdd10-131">3 bağlamalarla örnek</span><span class="sxs-lookup"><span data-stu-id="fdd10-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="fdd10-132">Yapılandırma dosyanıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fdd10-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="fdd10-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdd10-133">Example</span></span>

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
