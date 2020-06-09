---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598976"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="fb220-102">Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fb220-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="fb220-103"><xref:System.ServiceModel.WSFederationHttpBinding>yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="fb220-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="fb220-104">Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb220-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="fb220-105">Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fb220-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="fb220-106">Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb220-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="fb220-107">Ayrıca, koddaki bağlamayı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb220-107">You can also create the binding in code.</span></span> <span data-ttu-id="fb220-108">Oluşturulacak bağlama öğeleri yığınının bir açıklaması için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="fb220-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="fb220-109">HTTP ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fb220-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="fb220-110">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-110">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="fb220-111">Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="fb220-111">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="fb220-112">Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="fb220-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="fb220-113">Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="fb220-113">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="fb220-114">Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-114">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="fb220-115">Öğesini izleyerek [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) boş bir [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-115">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="fb220-116">Öğesini izleyerek [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) boş bir [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-116">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="fb220-117">Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fb220-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="fb220-118">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-118">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="fb220-119">Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="fb220-119">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="fb220-120">Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="fb220-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="fb220-121">Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="fb220-121">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="fb220-122">Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-122">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="fb220-123">TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fb220-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="fb220-124">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-124">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="fb220-125">Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="fb220-125">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="fb220-126">Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="fb220-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="fb220-127">Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="fb220-127">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="fb220-128">Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-128">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="fb220-129">Öğesini izleyerek [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) boş bir [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb220-129">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fb220-130">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="fb220-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="fb220-131">3 bağlamalarla örnek</span><span class="sxs-lookup"><span data-stu-id="fb220-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="fb220-132">Yapılandırma dosyanıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb220-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="fb220-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb220-133">Example</span></span>

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
