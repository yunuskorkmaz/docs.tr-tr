---
title: 'Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 86e7869efdba50d72cc61a1aebb767cf43927546
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795639"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="bcd69-102">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcd69-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="bcd69-103">Windows Communication Foundation (WCF) öğesinin *kimlik* özelliği, bir istemcinin beklenen hizmetin kimliğini önceden belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcd69-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="bcd69-104">Bir sunucu istemciye kendi kimliğini doğruladığında, kimlik beklenen kimliğe göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="bcd69-105">(Kimlik açıklaması ve nasıl çalıştığı hakkında bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="bcd69-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="bcd69-106">Gerekirse, doğrulama özel bir kimlik doğrulayıcı kullanılarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="bcd69-107">Örneğin, ek hizmet kimlik doğrulama denetimleri yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcd69-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="bcd69-108">Bu örnekte, özel kimlik doğrulayıcı sunucudan döndürülen X. 509.440 sertifikasındaki ek talepleri kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="bcd69-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="bcd69-109">Örnek bir uygulama için bkz. [hizmet kimliği örneği](../samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bcd69-109">For a sample application, see [Service Identity Sample](../samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="bcd69-110">EndpointIdentity sınıfını genişletmek için</span><span class="sxs-lookup"><span data-stu-id="bcd69-110">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="bcd69-111"><xref:System.ServiceModel.EndpointIdentity> Sınıfından türetilen yeni bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bcd69-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="bcd69-112">Bu örnek, uzantıyı `OrgEndpointIdentity`adlandırır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="bcd69-113">Hizmet tarafından döndürülen güvenlik belirtecindeki taleplerde kimlik denetimi gerçekleştirmek için genişletilmiş <xref:System.ServiceModel.Security.IdentityVerifier> sınıf tarafından kullanılan özelliklerle birlikte özel Üyeler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bcd69-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="bcd69-114">Bu örnek bir özelliği tanımlar: `OrganizationClaim` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bcd69-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="bcd69-115">IdentityVerifier sınıfını genişletmek için</span><span class="sxs-lookup"><span data-stu-id="bcd69-115">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="bcd69-116">Öğesinden <xref:System.ServiceModel.Security.IdentityVerifier>türetilen yeni bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bcd69-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="bcd69-117">Bu örnek, uzantıyı `CustomIdentityVerifier`adlandırır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="bcd69-118">Geçersiz kılma <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bcd69-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="bcd69-119">Yöntemi, kimlik denetiminin başarılı veya başarısız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="bcd69-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="bcd69-120">`CheckAccess` Yönteminde iki parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="bcd69-121">Birincisi, <xref:System.ServiceModel.EndpointIdentity> sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="bcd69-122">İkincisi, <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="bcd69-123">Yöntem uygulamasında, <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfının özelliği tarafından döndürülen talepler koleksiyonunu inceleyin ve gereken şekilde kimlik doğrulaması denetimleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="bcd69-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="bcd69-124">Bu örnek, "ayırt edici ad" türünde herhangi bir talep bularak başlar ve sonra adı <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`) uzantısıyla karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="bcd69-125">TryGetIdentity yöntemini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="bcd69-125">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="bcd69-126"><xref:System.ServiceModel.EndpointIdentity> Sınıfının bir örneğinin istemci tarafından döndürülüp döndürülmeyeceğini belirleyen yönteminiuygulayın.<xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="bcd69-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="bcd69-127">WCF altyapısı, önce hizmetin kimliğini iletiden almak `TryGetIdentity` için yönteminin uygulamasını çağırır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="bcd69-128">Sonra, altyapı `CheckAccess` uygulamayı döndürülen `EndpointIdentity` ve <xref:System.IdentityModel.Policy.AuthorizationContext>ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="bcd69-129">`TryGetIdentity` Yönteminde aşağıdaki kodu koyun:</span><span class="sxs-lookup"><span data-stu-id="bcd69-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="bcd69-130">Özel bir bağlama uygulamak ve özel IdentityVerifier ' i ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bcd69-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="bcd69-131">Bir <xref:System.ServiceModel.Channels.Binding> nesne döndüren bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bcd69-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="bcd69-132"><xref:System.ServiceModel.WSHttpBinding> Bu örnek <xref:System.ServiceModel.SecurityMode.Message>, sınıfının bir örneğini oluşturur ve güvenlik modunu ve <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageCredentialType.None>olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bcd69-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="bcd69-133">Yöntemini kullanarak bir <xref:System.ServiceModel.Channels.BindingElementCollection>oluşturun. <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A></span><span class="sxs-lookup"><span data-stu-id="bcd69-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="bcd69-134">Koleksiyondan ' i döndürün ve bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkenine atayın. <xref:System.ServiceModel.Channels.SecurityBindingElement></span><span class="sxs-lookup"><span data-stu-id="bcd69-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="bcd69-135">Sınıfının özelliğini daha önce oluşturulan `CustomIdentityVerifier` sınıfın yeni bir örneğine ayarlayın. <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> <xref:System.ServiceModel.Channels.LocalClientSecuritySettings></span><span class="sxs-lookup"><span data-stu-id="bcd69-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="bcd69-136">Döndürülen özel bağlama, istemci ve sınıfın bir örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcd69-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="bcd69-137">İstemci daha sonra aşağıdaki kodda gösterildiği gibi hizmete özel bir kimlik doğrulama denetimi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="bcd69-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="bcd69-138">Example</span></span>  
 <span data-ttu-id="bcd69-139">Aşağıdaki örnek, <xref:System.ServiceModel.Security.IdentityVerifier> sınıfının tamamen bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="bcd69-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="bcd69-140">Example</span></span>  
 <span data-ttu-id="bcd69-141">Aşağıdaki örnek, <xref:System.ServiceModel.EndpointIdentity> sınıfının tamamen bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcd69-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bcd69-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcd69-142">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="bcd69-143">Hizmet Kimliği Örneği</span><span class="sxs-lookup"><span data-stu-id="bcd69-143">Service Identity Sample</span></span>](../samples/service-identity-sample.md)
- [<span data-ttu-id="bcd69-144">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="bcd69-144">Authorization Policy</span></span>](../samples/authorization-policy.md)
