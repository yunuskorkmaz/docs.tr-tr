---
title: 'Nasıl yapılır: Yerel Yayımlayan Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 98d4c01bf2b84a6379eca5d0e1d5dbee68dc7cdd
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487145"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="395e3-102">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="395e3-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="395e3-103">Bu konuda verilen belirteçleri yerel yayımlayan kullanmak için bir istemciyi nasıl yapılandıracağınız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="395e3-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="395e3-104">Genellikle, bir istemci bir Federasyon Hizmeti ile iletişim kurduğunda, hizmet istemci belirteci vermek için beklenen belirteç hizmeti, federe hizmete kendi kimliğini doğrulamak için kullanacağı güvenlik adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="395e3-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="395e3-105">Belirli durumlarda istemci kullanmak için yapılandırılabilir bir *yerel yayımlayan*.</span><span class="sxs-lookup"><span data-stu-id="395e3-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 <span data-ttu-id="395e3-106">Windows Communication Foundation (WCF) kullanan yerel yayımlayan bir federe bağlama veren adresini olduğu durumlarda `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`.</span><span class="sxs-lookup"><span data-stu-id="395e3-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="395e3-107">Bu gibi durumlarda, yapılandırmanız gereken <xref:System.ServiceModel.Description.ClientCredentials> adresiyle yerel dağıtımcının ve bağlama bu veren ile iletişim kurmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="395e3-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="395e3-108">Varsa <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> özelliği `ClientCredentials` sınıf ayarlanmış `true`yerel yayımlayan adresi belirtilmedi ve veren adresi tarafından belirtilen [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federe bağlama `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, veya `null`, Windows CardSpace veren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="395e3-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="395e3-109">Kodu yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="395e3-109">To configure the local issuer in code</span></span>  
  
1. <span data-ttu-id="395e3-110">Türünde bir değişken oluşturma <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="395e3-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>  
  
2. <span data-ttu-id="395e3-111">Öğesinden döndürülen örneği için değişkeni ayarlayın <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> özelliği `ClientCredentials` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="395e3-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="395e3-112">Bu örnek tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği istemcinin (devralınan <xref:System.ServiceModel.ClientBase%601>) veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="395e3-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3. <span data-ttu-id="395e3-113">Ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> özelliğine yeni bir örneğini <xref:System.ServiceModel.EndpointAddress>, oluşturucusuna bağımsız değişken olarak yerel dağıtımcının adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="395e3-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="395e3-114">Alternatif olarak, yeni bir oluşturma <xref:System.Uri> oluşturucusuna bağımsız değişken olarak örneği.</span><span class="sxs-lookup"><span data-stu-id="395e3-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="395e3-115">`addressHeaders` Parametresi, bir dizi <xref:System.ServiceModel.Channels.AddressHeader> gösterildiği gibi örnekler.</span><span class="sxs-lookup"><span data-stu-id="395e3-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4. <span data-ttu-id="395e3-116">Kullanarak yerel sertifika verenin bağlamasını ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="395e3-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5. <span data-ttu-id="395e3-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="395e3-117">Optional.</span></span> <span data-ttu-id="395e3-118">Tarafından döndürülen bir koleksiyonda gibi davranışları ekleyerek yapılandırılmış uç nokta davranışları için yerel dağıtımcının ekleme <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="395e3-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="395e3-119">Yerel yayımlayan yapılandırma yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="395e3-119">To configure the local issuer in configuration</span></span>  
  
1. <span data-ttu-id="395e3-120">Oluşturma bir [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) öğesi alt öğesi olarak [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) kendisi bir alt öğesi olan öğeyi [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesinde bir uç nokta davranışı.</span><span class="sxs-lookup"><span data-stu-id="395e3-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2. <span data-ttu-id="395e3-121">Ayarlama `address` belirteci isteklerini kabul edecek yerel dağıtımcının adresine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="395e3-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3. <span data-ttu-id="395e3-122">Ayarlama `binding` ve `bindingConfiguration` öznitelikleri değerlerine başvuran yerel veren uç noktası ile iletişim kurarken kullanması için uygun bağlama.</span><span class="sxs-lookup"><span data-stu-id="395e3-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4. <span data-ttu-id="395e3-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="395e3-123">Optional.</span></span> <span data-ttu-id="395e3-124">Ayarlama [ \<kimlik >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesi alt öğesi olarak <`localIssuer`> öğesi ve yerel dağıtımcının için kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="395e3-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5. <span data-ttu-id="395e3-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="395e3-125">Optional.</span></span> <span data-ttu-id="395e3-126">Ayarlama [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) öğesi alt öğesi olarak <`localIssuer`> öğesi ve yerel dağıtımcının doğru bir şekilde çözmek için gerekli ek üstbilgi belirtin.</span><span class="sxs-lookup"><span data-stu-id="395e3-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="395e3-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="395e3-127">.NET Framework Security</span></span>  
 <span data-ttu-id="395e3-128">Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, yerel sertifika verenin bu bağlamayı kullanan uç noktaları için kullanılmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="395e3-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="395e3-129">Böyle bir bağlamanın kullanmayın veya veren adresi böylece bunlar bağlama değiştirme her zaman yerel dağıtımcının kullanmayı düşündüğünüz istemcileri sağlamak `null`.</span><span class="sxs-lookup"><span data-stu-id="395e3-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395e3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="395e3-130">See also</span></span>

- [<span data-ttu-id="395e3-131">Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="395e3-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="395e3-132">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="395e3-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="395e3-133">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="395e3-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
