---
title: "Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma"
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
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75200cc6aca424befe068a9dd718c6cc76492a91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="2dac4-102">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2dac4-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="2dac4-103">*Kimlik* özelliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] önceden hizmet beklenen kimliğini belirtmek bir istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dac4-103">The *identity* feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="2dac4-104">Sunucu istemciye kendi kimliğini doğrular her kimliği beklenen kimliğini karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="2dac4-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="2dac4-105">(Kimlik ve nasıl çalıştığı bir açıklaması için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="2dac4-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="2dac4-106">Gerekirse, doğrulama özel kimlik doğrulama kullanılarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2dac4-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="2dac4-107">Örneğin, ek hizmet kimlik doğrulama denetimleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dac4-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="2dac4-108">Bu örnekte, özel kimlik doğrulayıcı sunucusundan döndürülen X.509 sertifikası ek Taleplerde denetler.</span><span class="sxs-lookup"><span data-stu-id="2dac4-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="2dac4-109">Örnek bir uygulama için bkz: [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2dac4-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="2dac4-110">EndpointIdentity sınıfı genişletmek için</span><span class="sxs-lookup"><span data-stu-id="2dac4-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="2dac4-111">Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.EndpointIdentity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dac4-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="2dac4-112">Bu örnek uzantısı adları `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2dac4-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="2dac4-113">Özel üyelerin kullanılacak özellikleri birlikte eklemek genişletilmiş tarafından <xref:System.ServiceModel.Security.IdentityVerifier> hizmetten döndürülen güvenlik belirtecinizdeki talepleri karşı kimlik denetimi gerçekleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="2dac4-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="2dac4-114">Bu örnek bir özelliğini tanımlar: `OrganizationClaim` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2dac4-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="2dac4-115">IdentityVerifier sınıfı genişletmek için</span><span class="sxs-lookup"><span data-stu-id="2dac4-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="2dac4-116">Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="2dac4-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="2dac4-117">Bu örnek uzantısı adları `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="2dac4-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="2dac4-118">Geçersiz kılma <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dac4-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="2dac4-119">Yöntemi, kimlik denetimi başarılı veya başarısız olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="2dac4-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="2dac4-120">`CheckAccess` Yöntemi iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2dac4-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="2dac4-121">İlk örneği olan <xref:System.ServiceModel.EndpointIdentity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dac4-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="2dac4-122">İkinci örneği olan <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dac4-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="2dac4-123">Yöntem uygulamasında tarafından döndürülen talep koleksiyonunu inceleyin <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı ve gerektiği gibi kimlik doğrulama denetimleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="2dac4-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="2dac4-124">Bu örnekte, "Ayırt edici adı" türünde ve genişletilmesi adına karşılaştırır talep bularak başlar <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="2dac4-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="2dac4-125">TryGetIdentity yöntemi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="2dac4-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="2dac4-126">Uygulama <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> örneği olup olmadığını belirleyen yöntemi <xref:System.ServiceModel.EndpointIdentity> sınıfı istemci tarafından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="2dac4-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="2dac4-127">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Altyapı çağırır uygulanması `TryGetIdentity` ilk iletiden hizmetin kimliğini alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dac4-127">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="2dac4-128">Ardından, altyapı çağırır `CheckAccess` döndürülen uygulamasıyla `EndpointIdentity` ve <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="2dac4-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="2dac4-129">İçinde `TryGetIdentity` put yöntemi, aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="2dac4-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="2dac4-130">Özel bağlama uygulamak ve özel IdentityVerifier ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2dac4-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="2dac4-131">Döndüren bir yöntem oluşturma bir <xref:System.ServiceModel.Channels.Binding> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2dac4-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="2dac4-132">Bu örnek başlayan bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı ve güvenlik modunu ayarlar <xref:System.ServiceModel.SecurityMode.Message>ve kendi <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> için <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="2dac4-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="2dac4-133">Oluşturma bir <xref:System.ServiceModel.Channels.BindingElementCollection> kullanarak <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dac4-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="2dac4-134">Dönüş <xref:System.ServiceModel.Channels.SecurityBindingElement> koleksiyondan ve hangisine bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2dac4-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="2dac4-135">Ayarlama <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> özelliği <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> yeni bir örneğini sınıfına `CustomIdentityVerifier` daha önce oluşturduğunuz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dac4-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="2dac4-136">Döndürülen özel bağlama, sınıf ve istemci bir örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2dac4-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="2dac4-137">İstemci, daha sonra aşağıdaki kodda gösterildiği gibi bir özel kimlik doğrulama denetimi hizmetinin gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dac4-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2dac4-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dac4-138">Example</span></span>  
 <span data-ttu-id="2dac4-139">Aşağıdaki örnek, tam bir uygulama gösterir <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dac4-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2dac4-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dac4-140">Example</span></span>  
 <span data-ttu-id="2dac4-141">Aşağıdaki örnek, tam bir uygulama gösterir <xref:System.ServiceModel.EndpointIdentity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dac4-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2dac4-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dac4-142">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [<span data-ttu-id="2dac4-143">Hizmet kimliği örneği</span><span class="sxs-lookup"><span data-stu-id="2dac4-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [<span data-ttu-id="2dac4-144">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="2dac4-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="2dac4-145">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="2dac4-145">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
