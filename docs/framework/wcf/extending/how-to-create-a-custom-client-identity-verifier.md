---
title: 'Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: a7107e6e0bfdb948b584b5cbd57eafc3aff1bd59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569381"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="645ba-102">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="645ba-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="645ba-103">*Kimlik* Windows Communication Foundation (WCF) özelliği, beklenen hizmet kimliğini önceden belirtmek bir istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="645ba-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="645ba-104">Bir sunucu kendisini istemciye doğruladığında kimliği beklenen kimliğini karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="645ba-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="645ba-105">(Kimlik ve nasıl çalıştığı bir açıklaması için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="645ba-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="645ba-106">Gerekirse, doğrulama, bir özel kimlik doğrulama kullanılarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="645ba-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="645ba-107">Örneğin, ek hizmet kimlik doğrulama denetimleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="645ba-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="645ba-108">Bu örnekte, özel bir kimlik doğrulayıcı sunucusundan döndürülen X.509 sertifikasındaki ek talep denetler.</span><span class="sxs-lookup"><span data-stu-id="645ba-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="645ba-109">Örnek bir uygulama için bkz: [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="645ba-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="645ba-110">EndpointIdentity sınıfı genişletmek için</span><span class="sxs-lookup"><span data-stu-id="645ba-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="645ba-111">Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.EndpointIdentity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="645ba-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="645ba-112">Bu örnekte uzantı adları `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="645ba-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="645ba-113">Kullanılacak özellikleri birlikte özel üyeleri ekleme genişletilmiş tarafından <xref:System.ServiceModel.Security.IdentityVerifier> hizmetten döndürülen güvenlik belirtecinde talep karşı kimlik denetimi gerçekleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="645ba-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="645ba-114">Bu örnek, bir özellik tanımlar: `OrganizationClaim` özelliği.</span><span class="sxs-lookup"><span data-stu-id="645ba-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="645ba-115">IdentityVerifier sınıfı genişletmek için</span><span class="sxs-lookup"><span data-stu-id="645ba-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="645ba-116">Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="645ba-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="645ba-117">Bu örnekte uzantı adları `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="645ba-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="645ba-118">Geçersiz kılma <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="645ba-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="645ba-119">Yöntemi, kimlik denetimi başarılı veya başarısız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="645ba-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="645ba-120">`CheckAccess` Yöntemi iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="645ba-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="645ba-121">İlk örneğidir <xref:System.ServiceModel.EndpointIdentity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="645ba-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="645ba-122">İkinci örneğidir <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="645ba-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="645ba-123">Tarafından döndürülen talep koleksiyonunu yöntem uygulamasında incelemek <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı ve gerektiği gibi kimlik doğrulama denetimleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="645ba-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="645ba-124">Bu örnek türü "Ayırt edici ad" ve ardından uzantısını adına karşılaştırır talep bularak başlar <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="645ba-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="645ba-125">TryGetIdentity yöntemi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="645ba-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="645ba-126">Uygulama <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> örneği olup olmadığını belirleyen yöntemi <xref:System.ServiceModel.EndpointIdentity> sınıfı istemci tarafından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="645ba-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="645ba-127">WCF altyapısı uygulamasını çağırır `TryGetIdentity` önce gelen iletiyi hizmetin kimliğini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="645ba-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="645ba-128">Ardından, altyapı çağırır `CheckAccess` döndürülen uygulamasıyla `EndpointIdentity` ve <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="645ba-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="645ba-129">İçinde `TryGetIdentity` put yöntemi, aşağıdaki kodu:</span><span class="sxs-lookup"><span data-stu-id="645ba-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="645ba-130">Özel bağlama uygulamak ve özel IdentityVerifier ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="645ba-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="645ba-131">Döndüren bir yöntem oluşturma bir <xref:System.ServiceModel.Channels.Binding> nesne.</span><span class="sxs-lookup"><span data-stu-id="645ba-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="645ba-132">Bu örnekte başlayan bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlar <xref:System.ServiceModel.SecurityMode.Message>ve <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> için <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="645ba-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="645ba-133">Oluşturma bir <xref:System.ServiceModel.Channels.BindingElementCollection> kullanarak <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="645ba-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="645ba-134">Dönüş <xref:System.ServiceModel.Channels.SecurityBindingElement> koleksiyondan ve bunu bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkeni.</span><span class="sxs-lookup"><span data-stu-id="645ba-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="645ba-135">Ayarlama <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> özelliği <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> sınıfı için yeni bir örneğini `CustomIdentityVerifier` daha önce oluşturduğunuz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="645ba-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="645ba-136">Döndürülen özel bağlama, istemci ve sınıfı bir örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="645ba-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="645ba-137">Aşağıdaki kodda gösterildiği gibi istemci bir özel kimlik doğrulama denetimi hizmetinin daha sonra gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="645ba-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="645ba-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="645ba-138">Example</span></span>  
 <span data-ttu-id="645ba-139">Aşağıdaki örnek eksiksiz bir uygulamasını gösterir <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="645ba-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="645ba-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="645ba-140">Example</span></span>  
 <span data-ttu-id="645ba-141">Aşağıdaki örnek eksiksiz bir uygulamasını gösterir <xref:System.ServiceModel.EndpointIdentity> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="645ba-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="645ba-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="645ba-142">See also</span></span>
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="645ba-143">Hizmet Kimliği Örneği</span><span class="sxs-lookup"><span data-stu-id="645ba-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [<span data-ttu-id="645ba-144">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="645ba-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
- [<span data-ttu-id="645ba-145">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="645ba-145">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
