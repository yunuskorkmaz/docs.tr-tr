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
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972076"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="8a21d-102">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8a21d-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="8a21d-103">Bu konu, bir istemcinin verilen belirteçler için yerel bir veren kullanmak üzere nasıl yapılandırılacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a21d-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="8a21d-104">Genellikle, bir istemci federe bir hizmetle iletişim kurduğunda, hizmet istemcinin federasyon hizmetinde kimliğini doğrulamak için kullanacağı belirteci vermesi beklenen güvenlik belirteci hizmetinin adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a21d-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="8a21d-105">Belirli durumlarda, istemci *yerel bir veren*kullanmak üzere yapılandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a21d-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="8a21d-106">Windows Communication Foundation (WCF), Federasyon bağlamasının veren adresinin veya `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`olduğu durumlarda yerel bir veren kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a21d-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="8a21d-107">Bu gibi durumlarda, <xref:System.ServiceModel.Description.ClientCredentials> öğesini yerel veren adresiyle ve bu veren ile iletişim kurmak için kullanılacak bağlama ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a21d-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="8a21d-108">Sınıfının özelliği olarak ayarlandıysa`true`, yerel bir veren adresi belirtilmez ve [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federasyon bağlamasıyla belirtilen veren adresi <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, veya ise `null`, Windows CardSpace veren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a21d-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="8a21d-109">Kod içinde yerel sertifikayı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="8a21d-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="8a21d-110">Türünde değişken oluşturma<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="8a21d-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="8a21d-111">Değişkenini <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> `ClientCredentials` sınıfının özelliğinden döndürülen örneğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a21d-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="8a21d-112"><xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Bu örnek, istemcisinin özelliği (öğesinden <xref:System.ServiceModel.ClientBase%601>devralınmış) <xref:System.ServiceModel.ChannelFactory>veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği tarafından döndürülür:</span><span class="sxs-lookup"><span data-stu-id="8a21d-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="8a21d-113">Özelliğini, yerel veren 'in adresiyle <xref:System.ServiceModel.EndpointAddress>, oluşturucunun bir bağımsız değişkeni olarak yeni bir örneğine ayarlayın. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A></span><span class="sxs-lookup"><span data-stu-id="8a21d-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="8a21d-114">Alternatif olarak, Oluşturucu için <xref:System.Uri> bağımsız değişken olarak yeni bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a21d-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="8a21d-115">Parametresi, gösterildiği gibi bir <xref:System.ServiceModel.Channels.AddressHeader> örnek dizisidir. `addressHeaders`</span><span class="sxs-lookup"><span data-stu-id="8a21d-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="8a21d-116"><xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> Özelliğini kullanarak yerel veren için bağlamayı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a21d-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="8a21d-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8a21d-117">Optional.</span></span> <span data-ttu-id="8a21d-118"><xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> Özelliği tarafından döndürülen koleksiyona böyle davranışlar ekleyerek yerel veren için yapılandırılmış uç nokta davranışları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a21d-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="8a21d-119">Yapılandırmada yerel sertifikayı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="8a21d-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="8a21d-120">Bir uç nokta [davranışında \<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesinin bir alt öğesi olan [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesinin bir alt öğesi olarak bir [ \<LocalIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a21d-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="8a21d-121">Özniteliği, `address` belirteç isteklerini kabul edecek yerel veren adresi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a21d-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="8a21d-122">`binding` Ve`bindingConfiguration` özniteliklerini, yerel veren uç noktasıyla iletişim kurarken kullanılacak uygun bağlamaya başvuran değerlere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a21d-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="8a21d-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8a21d-123">Optional.</span></span> <span data-ttu-id="8a21d-124">Identity > öğesini <`localIssuer`> öğesinin bir alt öğesi olarak ayarlayın ve yerel veren için kimlik bilgilerini belirtin. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)</span><span class="sxs-lookup"><span data-stu-id="8a21d-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="8a21d-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8a21d-125">Optional.</span></span> <span data-ttu-id="8a21d-126">`localIssuer` [Üst > bilgileri < > öğesinin bir alt öğesi olarak ayarlayın ve yerel sertifikayı vereni doğru bir şekilde ele almak için gereken ek üstbilgileri belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)</span><span class="sxs-lookup"><span data-stu-id="8a21d-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="8a21d-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8a21d-127">.NET Framework Security</span></span>

<span data-ttu-id="8a21d-128">Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, bu bağlamayı kullanan uç noktalar için yerel veren kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8a21d-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="8a21d-129">Her zaman yerel vereni kullanması beklenen istemciler böyle bir bağlamayı kullanmamalıdır veya veren adresinin olması `null`için bağlamayı değiştirdiklerinden emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a21d-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a21d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a21d-130">See also</span></span>

- [<span data-ttu-id="8a21d-131">Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8a21d-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="8a21d-132">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a21d-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="8a21d-133">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a21d-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
