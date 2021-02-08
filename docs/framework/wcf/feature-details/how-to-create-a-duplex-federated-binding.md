---
description: 'Daha fazla bilgi edinin: nasıl yapılır: çift yönlü federe bağlama oluşturma'
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 92d5eeeffab88d88aa245b51738048dced2d5d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779913"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="6b5dc-103">Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b5dc-103">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="6b5dc-104"><xref:System.ServiceModel.WSFederationHttpBinding> yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-104"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="6b5dc-105">Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-105">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="6b5dc-106">Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-106">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="6b5dc-107">Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-107">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="6b5dc-108">Ayrıca, koddaki bağlamayı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-108">You can also create the binding in code.</span></span> <span data-ttu-id="6b5dc-109">Oluşturulacak bağlama öğeleri yığınının bir açıklaması için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="6b5dc-109">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="6b5dc-110">HTTP ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6b5dc-110">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="6b5dc-111">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-111">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="6b5dc-112">Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-112">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="6b5dc-113">Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-113">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="6b5dc-114">Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-114">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="6b5dc-115">Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-115">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="6b5dc-116">Öğesini izleyerek [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) boş bir [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-116">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="6b5dc-117">Öğesini izleyerek [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) boş bir [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-117">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="6b5dc-118">Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6b5dc-118">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="6b5dc-119">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-119">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="6b5dc-120">Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-120">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="6b5dc-121">Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-121">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="6b5dc-122">Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-122">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="6b5dc-123">Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-123">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="6b5dc-124">TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6b5dc-124">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="6b5dc-125">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma dosyasının düğümünde bir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-125">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="6b5dc-126">Öğesinin içinde [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) , [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) özniteliği olarak ayarlanmış bir öğe oluşturun `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-126">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="6b5dc-127">Öğesinin içinde [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) , [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) özniteliği olarak ayarlanmış bir öğe oluşturun `authenticationMode` `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-127">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="6b5dc-128">Öğesinin içinde [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) , [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` veya olarak ayarlanan özniteliği olan bir öğe oluşturun `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="6b5dc-128">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="6b5dc-129">Öğesini izleyerek [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) boş bir [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-129">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="6b5dc-130">Öğesini izleyerek [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) boş bir [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-130">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6b5dc-131">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="6b5dc-131">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="6b5dc-132">3 bağlamalarla örnek</span><span class="sxs-lookup"><span data-stu-id="6b5dc-132">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="6b5dc-133">Yapılandırma dosyanıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6b5dc-133">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="6b5dc-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b5dc-134">Example</span></span>

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
