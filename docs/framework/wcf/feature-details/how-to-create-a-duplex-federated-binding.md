---
title: 'Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972055"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="bcf92-102">Nasıl yapılır: Çift Yönlü Federe Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcf92-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="bcf92-103"><xref:System.ServiceModel.WSFederationHttpBinding>yalnızca veri birimini ve istek/yanıt iletisi değişimi sözleşmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="bcf92-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="bcf92-104">Çift yönlü ileti değişimi sözleşmesini kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bcf92-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="bcf92-105">Aşağıdaki yordamlarda bunun nasıl yapılacağı, HTTP ve TCP aktarımları için Ileti modu güvenliğinin kullanılması ve TCP aktarımı için karışık mod güvenliği kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bcf92-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="bcf92-106">Tüm 3 bağlamaları gösteren örnek kod bu konunun sonunda yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bcf92-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="bcf92-107">Ayrıca, koddaki bağlamayı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcf92-107">You can also create the binding in code.</span></span> <span data-ttu-id="bcf92-108">Oluşturulacak bağlama öğeleri yığınının bir açıklaması için bkz [. nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)kullanarak özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bcf92-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="bcf92-109">HTTP ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bcf92-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="bcf92-110">Yapılandırma dosyasının [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlamalar > düğümünde bir CustomBinding > öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="bcf92-111">CustomBinding > öğesinin içinde, `name` özniteliği olarak ayarlanmış`FederationDuplexHttpMessageSecurityBinding`bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="bcf92-112">Bağlama > öğesinin içinde, `authenticationMode` özniteliği olarak ayarlanmış`SecureConversation`bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun. [ \<](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="bcf92-113">[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` `IssuedTokenForCertificate` [ Güvenlik>öğesiiçinde,veyaolarakayarlananözniteliğiilebirsecurebir\<Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesioluşturun`IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="bcf92-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="bcf92-114">Güvenlik > öğesini izleyerek boş [ \<bir CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="bcf92-115">CompositeDuplex > öğeden sonra boş [ \<bir oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="bcf92-116">OneWay > öğesini izleyerek boş [ \<bir HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="bcf92-117">Çift yönlü federe özel bağlamayı TCP ileti güvenliği moduyla oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bcf92-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="bcf92-118">Yapılandırma dosyasının [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlamalar > düğümünde bir CustomBinding > öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="bcf92-119">CustomBinding > öğesinin içinde, `name` özniteliği olarak ayarlanmış`FederationDuplexTcpMessageSecurityBinding`bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="bcf92-120">Bağlama > öğesinin içinde, `authenticationMode` özniteliği olarak ayarlanmış`SecureConversation`bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun. [ \<](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="bcf92-121">[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` `IssuedTokenForCertificate` [ Güvenlik>öğesiiçinde,veyaolarakayarlananözniteliğiilebirsecurebir\<Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesioluşturun`IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="bcf92-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="bcf92-122">Güvenlik > öğesini izleyerek boş [ \<bir TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="bcf92-123">TCP karma güvenlik modu ile çift yönlü federe özel bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bcf92-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="bcf92-124">Yapılandırma dosyasının [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bağlamalar > düğümünde bir CustomBinding > öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="bcf92-125">CustomBinding > öğesinin içinde, `name` özniteliği olarak ayarlanmış`FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="bcf92-126">Bağlama > öğesinin içinde, `authenticationMode` özniteliği olarak ayarlanmış`SecureConversation`bir [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi oluşturun. [ \<](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="bcf92-127">[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` `IssuedTokenForCertificate` [ Güvenlik>öğesiiçinde,veyaolarakayarlananözniteliğiilebirsecurebir\<Bootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesioluşturun`IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="bcf92-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="bcf92-128">Güvenlik > öğesini izleyerek boş [ \<bir sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="bcf92-129">SslStreamSecurity > öğesini izleyerek boş [ \<bir TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) öğesi oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="bcf92-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bcf92-130">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="bcf92-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="bcf92-131">3 bağlamalarla örnek</span><span class="sxs-lookup"><span data-stu-id="bcf92-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="bcf92-132">Yapılandırma dosyanıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bcf92-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="bcf92-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="bcf92-133">Example</span></span>

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
