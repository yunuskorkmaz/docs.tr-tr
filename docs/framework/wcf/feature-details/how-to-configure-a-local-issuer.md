---
title: "Nasıl yapılır: Yerel Yayımlayan Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 413f534bacd1f5551cd3b5d7c83e3722104fa0c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="47b2a-102">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47b2a-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="47b2a-103">Bu konu, istemciyi yerel yayımlayan verilen belirteçleri kullanacak şekilde yapılandırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="47b2a-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="47b2a-104">Genellikle, bir istemci bir Federasyon Hizmeti ile iletişim kurduğunda, hizmet istemci belirteci vermek için beklenen belirteci hizmeti kendisini Federasyon Hizmeti için kimlik doğrulaması için kullanacağınız güvenlik adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47b2a-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="47b2a-105">Belirli durumlarda, istemci kullanmak için yapılandırılabilir bir *yerel yayımlayan*.</span><span class="sxs-lookup"><span data-stu-id="47b2a-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="47b2a-106">Yerel yayımlayan bir federe bağlama veren adresini http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous olduğu durumlarda kullanır veya `null`.</span><span class="sxs-lookup"><span data-stu-id="47b2a-106"> uses a local issuer in cases where the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`.</span></span> <span data-ttu-id="47b2a-107">Böyle durumlarda, yapılandırmalısınız <xref:System.ServiceModel.Description.ClientCredentials> adresi bu veren ile iletişim kurmak için kullanılacak yerel yayımlayan ve bağlama ile.</span><span class="sxs-lookup"><span data-stu-id="47b2a-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47b2a-108">Varsa <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> özelliği `ClientCredentials` sınıfı ayarlanmış `true`, yerel veren adresi belirtilmedi ve veren adresi tarafından belirtilen [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federe bağlama olduğu http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, veya `null`, sonra Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] veren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47b2a-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, or is `null`, then the Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="47b2a-109">Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47b2a-109">To configure the local issuer in code</span></span>  
  
1.  <span data-ttu-id="47b2a-110">Türünde bir değişken oluşturma<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="47b2a-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>  
  
2.  <span data-ttu-id="47b2a-111">Döndürülen örneğine değişkenini <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> özelliği `ClientCredentials` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="47b2a-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="47b2a-112">Bu örnek tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği istemcinin (devralınan <xref:System.ServiceModel.ClientBase%601>) veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="47b2a-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <span data-ttu-id="47b2a-113">Ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> yeni bir örneğini özelliğine <xref:System.ServiceModel.EndpointAddress>, oluşturucuya bağımsız değişken olarak yerel verenin adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="47b2a-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="47b2a-114">Alternatif olarak, yeni bir oluşturun <xref:System.Uri> oluşturucu bağımsız değişken olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="47b2a-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="47b2a-115">`addressHeaders` Parametredir bir dizi <xref:System.ServiceModel.Channels.AddressHeader> gösterildiği gibi örnekleri.</span><span class="sxs-lookup"><span data-stu-id="47b2a-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <span data-ttu-id="47b2a-116">Kullanarak yerel yayımlayan için bağlama ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="47b2a-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  <span data-ttu-id="47b2a-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="47b2a-117">Optional.</span></span> <span data-ttu-id="47b2a-118">Yapılandırılmış uç noktası davranışları yerel vericisi gibi davranışları tarafından döndürülen koleksiyonuna ekleyerek <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="47b2a-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="47b2a-119">Yerel yayımlayan yapılandırma yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="47b2a-119">To configure the local issuer in configuration</span></span>  
  
1.  <span data-ttu-id="47b2a-120">Oluşturma bir [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) öğesi bir alt öğesi olarak [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) kendisini bir alt öğesi olan öğeyi [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) bir uç noktası davranışı öğesinde.</span><span class="sxs-lookup"><span data-stu-id="47b2a-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2.  <span data-ttu-id="47b2a-121">Ayarlama `address` belirteç istekleri kabul edecek yerel yayımlayan adresine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="47b2a-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3.  <span data-ttu-id="47b2a-122">Ayarlama `binding` ve `bindingConfiguration` öznitelikleri yerel yayımlayan bitiş noktası ile iletişim kurarken kullanmak üzere uygun bağlama başvuru değerleri.</span><span class="sxs-lookup"><span data-stu-id="47b2a-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4.  <span data-ttu-id="47b2a-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="47b2a-123">Optional.</span></span> <span data-ttu-id="47b2a-124">Ayarlama [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesi bir alt öğesi olarak <`localIssuer`> öğesi ve yerel veren kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="47b2a-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5.  <span data-ttu-id="47b2a-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="47b2a-125">Optional.</span></span> <span data-ttu-id="47b2a-126">Ayarlama [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) öğesi bir alt öğesi olarak <`localIssuer`> öğesi ve doğru yerel yayımlayan değinmek için gerekli ek üstbilgi belirtin.</span><span class="sxs-lookup"><span data-stu-id="47b2a-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="47b2a-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="47b2a-127">.NET Framework Security</span></span>  
 <span data-ttu-id="47b2a-128">Bir veren adresi ve bağlama için belirtilen bir bağlama belirtilirse, yerel yayımlayan bu bağlamayı kullanan uç noktaları için kullanılıp kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47b2a-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="47b2a-129">Her zaman yerel yayımlayan kullanmayı düşündüğünüz istemcileri sağlamak veren adresi böylece bunlar bağlama değiştirmek veya böyle bir bağlama kullanmayın `null`.</span><span class="sxs-lookup"><span data-stu-id="47b2a-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b2a-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47b2a-130">See Also</span></span>  
 [<span data-ttu-id="47b2a-131">Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın</span><span class="sxs-lookup"><span data-stu-id="47b2a-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="47b2a-132">Nasıl yapılır: federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="47b2a-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="47b2a-133">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="47b2a-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
