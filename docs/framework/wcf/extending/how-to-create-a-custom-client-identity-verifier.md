---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel Istemci Kimliği Doğrulayıcı oluşturma'
title: 'Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: ee0cff59d877fbb6cd636f831cfccf4f51a3ab40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743700"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="2db7c-103">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2db7c-103">How to: Create a Custom Client Identity Verifier</span></span>

<span data-ttu-id="2db7c-104">Windows Communication Foundation (WCF) öğesinin *kimlik* özelliği, bir istemcinin beklenen hizmetin kimliğini önceden belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2db7c-104">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="2db7c-105">Bir sunucu istemciye kendi kimliğini doğruladığında, kimlik beklenen kimliğe göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="2db7c-105">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="2db7c-106">(Kimlik açıklaması ve nasıl çalıştığı hakkında bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="2db7c-106">(For an explanation of identity and how it works, see [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="2db7c-107">Gerekirse, doğrulama özel bir kimlik doğrulayıcı kullanılarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2db7c-107">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="2db7c-108">Örneğin, ek hizmet kimlik doğrulama denetimleri yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2db7c-108">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="2db7c-109">Bu örnekte, özel kimlik doğrulayıcı sunucudan döndürülen X. 509.440 sertifikasındaki ek talepleri kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="2db7c-109">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="2db7c-110">Örnek bir uygulama için bkz. [hizmet kimliği örneği](../samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2db7c-110">For a sample application, see [Service Identity Sample](../samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="2db7c-111">EndpointIdentity sınıfını genişletmek için</span><span class="sxs-lookup"><span data-stu-id="2db7c-111">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="2db7c-112">Sınıfından türetilen yeni bir sınıf tanımlayın <xref:System.ServiceModel.EndpointIdentity> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-112">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="2db7c-113">Bu örnek, uzantıyı adlandırır `OrgEndpointIdentity` .</span><span class="sxs-lookup"><span data-stu-id="2db7c-113">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="2db7c-114"><xref:System.ServiceModel.Security.IdentityVerifier>Hizmet tarafından döndürülen güvenlik belirtecindeki taleplerde kimlik denetimi gerçekleştirmek için genişletilmiş sınıf tarafından kullanılan özelliklerle birlikte özel Üyeler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2db7c-114">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="2db7c-115">Bu örnek bir özelliği tanımlar: `OrganizationClaim` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2db7c-115">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="2db7c-116">IdentityVerifier sınıfını genişletmek için</span><span class="sxs-lookup"><span data-stu-id="2db7c-116">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="2db7c-117">Öğesinden türetilen yeni bir sınıf tanımlayın <xref:System.ServiceModel.Security.IdentityVerifier> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-117">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="2db7c-118">Bu örnek, uzantıyı adlandırır `CustomIdentityVerifier` .</span><span class="sxs-lookup"><span data-stu-id="2db7c-118">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="2db7c-119">Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-119">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="2db7c-120">Yöntemi, kimlik denetiminin başarılı veya başarısız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="2db7c-120">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="2db7c-121">`CheckAccess`Yönteminde iki parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="2db7c-121">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="2db7c-122">Birincisi, sınıfının bir örneğidir <xref:System.ServiceModel.EndpointIdentity> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-122">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="2db7c-123">İkincisi, sınıfının bir örneğidir <xref:System.IdentityModel.Policy.AuthorizationContext> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-123">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="2db7c-124">Yöntem uygulamasında, sınıfının özelliği tarafından döndürülen talepler koleksiyonunu inceleyin <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> ve gereken şekilde kimlik doğrulaması denetimleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="2db7c-124">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="2db7c-125">Bu örnek, "ayırt edici ad" türünde herhangi bir talep bularak başlar ve sonra adı <xref:System.ServiceModel.EndpointIdentity> () uzantısıyla karşılaştırır `OrgEndpointIdentity` .</span><span class="sxs-lookup"><span data-stu-id="2db7c-125">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="2db7c-126">TryGetIdentity yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="2db7c-126">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="2db7c-127"><xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A>Sınıfının bir örneğinin <xref:System.ServiceModel.EndpointIdentity> istemci tarafından döndürülüp döndürülmeyeceğini belirleyen yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2db7c-127">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="2db7c-128">WCF altyapısı, `TryGetIdentity` önce hizmetin kimliğini iletiden almak için yönteminin uygulamasını çağırır.</span><span class="sxs-lookup"><span data-stu-id="2db7c-128">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="2db7c-129">Sonra, altyapı `CheckAccess` uygulamayı döndürülen ve ile çağırır `EndpointIdentity` <xref:System.IdentityModel.Policy.AuthorizationContext> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-129">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="2db7c-130">`TryGetIdentity`Yönteminde aşağıdaki kodu koyun:</span><span class="sxs-lookup"><span data-stu-id="2db7c-130">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="2db7c-131">Özel bir bağlama uygulamak ve özel IdentityVerifier ' i ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2db7c-131">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="2db7c-132">Bir nesne döndüren bir yöntem oluşturun <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-132">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="2db7c-133">Bu örnek, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> ve güvenlik modunu ve olarak ayarlar <xref:System.ServiceModel.SecurityMode.Message> <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageCredentialType.None> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-133">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="2db7c-134"><xref:System.ServiceModel.Channels.BindingElementCollection>Yöntemini kullanarak bir oluşturun <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-134">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="2db7c-135"><xref:System.ServiceModel.Channels.SecurityBindingElement>Koleksiyondan ' i döndürün ve bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="2db7c-135">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="2db7c-136"><xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> Sınıfının özelliğini `CustomIdentityVerifier` daha önce oluşturulan sınıfın yeni bir örneğine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2db7c-136">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="2db7c-137">Döndürülen özel bağlama, istemci ve sınıfın bir örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2db7c-137">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="2db7c-138">İstemci daha sonra aşağıdaki kodda gösterildiği gibi hizmete özel bir kimlik doğrulama denetimi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2db7c-138">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2db7c-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="2db7c-139">Example</span></span>  

 <span data-ttu-id="2db7c-140">Aşağıdaki örnek, sınıfının tamamen bir uygulamasını gösterir <xref:System.ServiceModel.Security.IdentityVerifier> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-140">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2db7c-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="2db7c-141">Example</span></span>  

 <span data-ttu-id="2db7c-142">Aşağıdaki örnek, sınıfının tamamen bir uygulamasını gösterir <xref:System.ServiceModel.EndpointIdentity> .</span><span class="sxs-lookup"><span data-stu-id="2db7c-142">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2db7c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2db7c-143">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="2db7c-144">Hizmet Kimliği Örneği</span><span class="sxs-lookup"><span data-stu-id="2db7c-144">Service Identity Sample</span></span>](../samples/service-identity-sample.md)
- [<span data-ttu-id="2db7c-145">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="2db7c-145">Authorization Policy</span></span>](../samples/authorization-policy.md)
