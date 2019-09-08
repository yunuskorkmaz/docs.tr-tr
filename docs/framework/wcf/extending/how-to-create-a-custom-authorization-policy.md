---
title: 'Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 5d5268cd2171bdccc3885cd599fdc8c277e61aa4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795704"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="f6c2f-102">Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6c2f-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="f6c2f-103">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, talep tabanlı bir yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="f6c2f-104">Talepler belirteçlerden ayıklanır, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenir ve ardından, yetkilendirme kararları <xref:System.IdentityModel.Policy.AuthorizationContext> almak için incelenebilir bir öğesine yerleştirildi.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="f6c2f-105">Özel bir ilke, gelen belirteçlerdeki talepleri uygulama tarafından beklenen talebe dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="f6c2f-106">Bu şekilde, uygulama katmanı, WCF 'nin desteklediği farklı belirteç türleri tarafından sunulan farklı talepler hakkında ayrıntılardan ayrı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="f6c2f-107">Bu konu, özel bir yetkilendirme ilkesinin nasıl uygulanacağını ve bu ilkenin bir hizmet tarafından kullanılan ilkeler koleksiyonuna nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="f6c2f-108">Özel bir yetkilendirme ilkesi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f6c2f-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="f6c2f-109">Öğesinden <xref:System.IdentityModel.Policy.IAuthorizationPolicy>türetilen yeni bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="f6c2f-110">Sınıf için oluşturucuda benzersiz bir <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> dize oluşturup salt okunurdur ve özelliğe her erişildiğinde bu dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="f6c2f-111">İlke vereni temsil eden bir <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> <xref:System.IdentityModel.Claims.ClaimSet> döndüren salt okunurdur özelliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="f6c2f-112">Bu, uygulamayı veya `ClaimSet` yerleşik `ClaimSet` bir özelliği `ClaimSet` (örneğin, statik <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özellik tarafından döndürülen) temsil eden bir olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="f6c2f-113"><xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> Yöntemini aşağıdaki yordamda açıklandığı gibi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="f6c2f-114">Değerlendir metodunu uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f6c2f-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="f6c2f-115">Bu yönteme iki parametre geçirilir: <xref:System.IdentityModel.Policy.EvaluationContext> sınıfın bir örneği ve bir nesne başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="f6c2f-116">Özel yetkilendirme <xref:System.IdentityModel.Claims.ClaimSet> ilkesi, <xref:System.IdentityModel.Policy.EvaluationContext>öğesinin geçerli içeriğiyle ilgili olmayan örnekler eklerse, <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemini çağırarak ve <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yönteminden geri dönerek `true` her `ClaimSet` birini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="f6c2f-117">Döndürme `true` , yetkilendirme ilkesinin işini gerçekleştirdiği yetkilendirme altyapısına ve yeniden çağrılması gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="f6c2f-118">Özel yetkilendirme ilkesi yalnızca içinde `EvaluationContext`belirli talepler zaten mevcutsa talep kümelerini eklerse, <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> özelliği tarafından döndürülen `ClaimSet` örnekleri inceleyerek bu talepler için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="f6c2f-119">Talepler varsa, <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemini çağırarak yeni talep kümelerini ekleyin ve daha fazla talep kümesi eklenmek için, geri dönüş `true`, yetkilendirme ilkesinin işini tamamladığı yetkilendirme altyapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="f6c2f-120">Talepler yoksa, diğer yetkilendirme ilkeleri `false` `EvaluationContext`öğesine daha fazla talep kümesi ekse, yetkilendirme ilkesinin tekrar çağrılması gerektiğini belirten döndürün.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="f6c2f-121">Daha karmaşık işleme senaryolarında, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemin ikinci parametresi, belirli bir değerlendirme için <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yönteme yapılan her bir çağrı sırasında yetkilendirme altyapısının geri geçidizin olacağı bir durum değişkenini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="f6c2f-122">Yapılandırma yoluyla özel bir yetkilendirme ilkesi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="f6c2f-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="f6c2f-123">Öğe içindeki öğesindeki öğesinde `policyType` bulunan özniteliğinde `add` `authorizationPolicies` `serviceAuthorization` özel yetkilendirme ilkesi türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="f6c2f-124">Kodla özel bir yetkilendirme ilkesi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="f6c2f-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="f6c2f-125">' A <xref:System.Collections.Generic.List%601> <xref:System.IdentityModel.Policy.IAuthorizationPolicy>oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="f6c2f-126">Özel yetkilendirme ilkesinin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="f6c2f-127">Yetkilendirme ilkesi örneğini listeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="f6c2f-128">Her özel yetkilendirme ilkesi için adım 2 ve 3 ' ü yineleyin.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="f6c2f-129">Özelliğe, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> listenin salt okunurdur bir sürümünü atayın.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="f6c2f-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6c2f-130">Example</span></span>  
 <span data-ttu-id="f6c2f-131">Aşağıdaki örnek, tüm <xref:System.IdentityModel.Policy.IAuthorizationPolicy> bir uygulamayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f6c2f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6c2f-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="f6c2f-133">Nasıl yapılır: Talepleri Karşılaştır</span><span class="sxs-lookup"><span data-stu-id="f6c2f-133">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="f6c2f-134">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6c2f-134">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="f6c2f-135">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="f6c2f-135">Authorization Policy</span></span>](../samples/authorization-policy.md)
