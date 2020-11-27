---
title: 'Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: fef7aa531c946ecacef30bb79f2362bad4d375ed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256033"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="54524-102">Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54524-102">How to: Create a Custom Authorization Policy</span></span>

<span data-ttu-id="54524-103">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, talep tabanlı bir yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="54524-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="54524-104">Talepler belirteçlerden ayıklanır, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenir ve ardından, <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları almak için incelenebilir bir öğesine yerleştirildi.</span><span class="sxs-lookup"><span data-stu-id="54524-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="54524-105">Özel bir ilke, gelen belirteçlerdeki talepleri uygulama tarafından beklenen talebe dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54524-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="54524-106">Bu şekilde, uygulama katmanı, WCF 'nin desteklediği farklı belirteç türleri tarafından sunulan farklı talepler hakkında ayrıntılardan ayrı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54524-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="54524-107">Bu konu, özel bir yetkilendirme ilkesinin nasıl uygulanacağını ve bu ilkenin bir hizmet tarafından kullanılan ilkeler koleksiyonuna nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54524-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="54524-108">Özel bir yetkilendirme ilkesi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="54524-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="54524-109">Öğesinden türetilen yeni bir sınıf tanımlayın <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .</span><span class="sxs-lookup"><span data-stu-id="54524-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="54524-110"><xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A>Sınıf için oluşturucuda benzersiz bir dize oluşturup salt okunurdur ve özelliğe her erişildiğinde bu dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="54524-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="54524-111"><xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>İlke vereni temsil eden bir döndüren salt okunurdur özelliğini uygulayın <xref:System.IdentityModel.Claims.ClaimSet> .</span><span class="sxs-lookup"><span data-stu-id="54524-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="54524-112">Bu, `ClaimSet` uygulamayı veya yerleşik bir `ClaimSet` Özelliği (örneğin, `ClaimSet` statik özellik tarafından döndürülen) temsil eden bir olabilir <xref:System.IdentityModel.Claims.ClaimSet.System%2A> .</span><span class="sxs-lookup"><span data-stu-id="54524-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="54524-113"><xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>Yöntemini aşağıdaki yordamda açıklandığı gibi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="54524-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="54524-114">Değerlendir metodunu uygulamak için</span><span class="sxs-lookup"><span data-stu-id="54524-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="54524-115">Bu yönteme iki parametre geçirilir: sınıfın bir örneği <xref:System.IdentityModel.Policy.EvaluationContext> ve bir nesne başvurusu.</span><span class="sxs-lookup"><span data-stu-id="54524-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="54524-116">Özel yetkilendirme ilkesi <xref:System.IdentityModel.Claims.ClaimSet> , öğesinin geçerli içeriğiyle ilgili olmayan örnekler eklerse <xref:System.IdentityModel.Policy.EvaluationContext> , `ClaimSet` <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemini çağırarak ve yönteminden geri dönerek her birini ekleyin `true` <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> .</span><span class="sxs-lookup"><span data-stu-id="54524-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="54524-117">Döndürme, yetkilendirme `true` ilkesinin işini gerçekleştirdiği yetkilendirme altyapısına ve yeniden çağrılması gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54524-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="54524-118">Özel yetkilendirme ilkesi yalnızca içinde belirli talepler zaten mevcutsa talep kümelerini eklerse `EvaluationContext` , `ClaimSet` özelliği tarafından döndürülen örnekleri inceleyerek bu talepler için arama yapın <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> .</span><span class="sxs-lookup"><span data-stu-id="54524-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="54524-119">Talepler varsa, yöntemini çağırarak yeni talep kümelerini ekleyin <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> ve daha fazla talep kümesi eklenmek için, geri dönüş `true` , yetkilendirme ilkesinin işini tamamladığı yetkilendirme altyapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54524-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="54524-120">Talepler yoksa, `false` diğer yetkilendirme ilkeleri öğesine daha fazla talep kümesi ekse, yetkilendirme ilkesinin tekrar çağrılması gerektiğini belirten döndürün `EvaluationContext` .</span><span class="sxs-lookup"><span data-stu-id="54524-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="54524-121">Daha karmaşık işleme senaryolarında, yöntemin ikinci parametresi, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> belirli bir değerlendirme için yönteme yapılan her bir çağrı sırasında yetkilendirme altyapısının geri geçidizin olacağı bir durum değişkenini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54524-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="54524-122">Yapılandırma yoluyla özel bir yetkilendirme ilkesi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="54524-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="54524-123">Öğe içindeki öğesindeki öğesinde bulunan özniteliğinde özel yetkilendirme ilkesi türünü belirtin `policyType` `add` `authorizationPolicies` `serviceAuthorization` .</span><span class="sxs-lookup"><span data-stu-id="54524-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="54524-124">Kodla özel bir yetkilendirme ilkesi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="54524-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="54524-125">' A <xref:System.Collections.Generic.List%601> oluşturun <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .</span><span class="sxs-lookup"><span data-stu-id="54524-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="54524-126">Özel yetkilendirme ilkesinin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54524-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="54524-127">Yetkilendirme ilkesi örneğini listeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54524-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="54524-128">Her özel yetkilendirme ilkesi için adım 2 ve 3 ' ü yineleyin.</span><span class="sxs-lookup"><span data-stu-id="54524-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="54524-129">Özelliğe, listenin salt okunurdur bir sürümünü atayın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> .</span><span class="sxs-lookup"><span data-stu-id="54524-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="54524-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="54524-130">Example</span></span>  

 <span data-ttu-id="54524-131">Aşağıdaki örnek, tüm bir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulamayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="54524-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="54524-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54524-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="54524-133">Nasıl yapılır: Talepleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="54524-133">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="54524-134">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54524-134">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="54524-135">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="54524-135">Authorization Policy</span></span>](../samples/authorization-policy.md)
