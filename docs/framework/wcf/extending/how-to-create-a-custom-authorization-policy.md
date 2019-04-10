---
title: 'Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 05130e809356369ee2b43d9af86acf69fe527e9a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295425"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="ac841-102">Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac841-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="ac841-103">Windows Communication Foundation (WCF) kimlik modeli altyapısı, bir talep tabanlı yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="ac841-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="ac841-104">Talep belirteçleri ayıklanan, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenen ve ardından yerleştirilip bir <xref:System.IdentityModel.Policy.AuthorizationContext> , ardından incelenebilir yetkilendirme kararları vermek için.</span><span class="sxs-lookup"><span data-stu-id="ac841-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="ac841-105">Özel bir ilke, uygulama tarafından beklenen talep gelen belirteçleri gelen talepleri dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac841-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="ac841-106">Bu şekilde, uygulama katmanı WCF desteklediği farklı belirteç türleri tarafından sunulan farklı talepleri ayrıntılarından yalıtılmış.</span><span class="sxs-lookup"><span data-stu-id="ac841-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="ac841-107">Bu konuda, bir hizmet tarafından kullanılan ilkeleri koleksiyonunu Bu ilkeyi ekleme ve özel yetkilendirme ilkesi uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac841-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="ac841-108">Özel yetkilendirme ilkesi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="ac841-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="ac841-109">Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ac841-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="ac841-110">Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> özelliği erişildiğinde sınıf için oluşturucu içinde benzersiz bir dize oluşturma ve bu dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="ac841-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="ac841-111">Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> döndürerek özelliği bir <xref:System.IdentityModel.Claims.ClaimSet> ilke veren temsil eden.</span><span class="sxs-lookup"><span data-stu-id="ac841-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="ac841-112">Bunun bir `ClaimSet` temsil eden bir uygulama veya yerleşik bir `ClaimSet` (örneğin, `ClaimSet` özelliğinden döndürülen statik <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ac841-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="ac841-113">Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> aşağıdaki yordamda açıklandığı şekilde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ac841-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="ac841-114">Evaluate yöntemi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="ac841-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="ac841-115">İki parametre, bu yönteme geçirilir: örneği <xref:System.IdentityModel.Policy.EvaluationContext> sınıfı ve bir nesne başvurusu.</span><span class="sxs-lookup"><span data-stu-id="ac841-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="ac841-116">Özel yetkilendirme ilkesi eklerse <xref:System.IdentityModel.Claims.ClaimSet> örnekleri geçerli içeriğini bakılmaksızın <xref:System.IdentityModel.Policy.EvaluationContext>, her ekleme `ClaimSet` çağırarak <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve dönüş `true` gelen <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ac841-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="ac841-117">Döndüren `true` yetkilendirme ilkesi işini yürüttü ve yeniden çağrılması gerekmez yetkilendirme altyapısında gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac841-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="ac841-118">Yalnızca belirli talep zaten varsa, özel yetkilendirme ilkesi talep kümelerinin eklerse, `EvaluationContext`, sonra bu talepleri için inceleyerek bakın `ClaimSet` tarafından döndürülen örnek <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ac841-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="ac841-119">Talep mevcut olması durumunda, ardından yeni bir talep ayarlar çağırarak ekleyin <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve artık kümeleridir eklendi, iade edilecek talep if `true`yetkilendirme ilkesi çalışmasını tamamlamadan yetkilendirme altyapısına gösteren.</span><span class="sxs-lookup"><span data-stu-id="ac841-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="ac841-120">Talep mevcut değilse, dönüş `false`, talep kümeleri için daha fazla diğer yetkilendirme ilkeleri eklerseniz, Yetkilendirme İlkesi'nin yeniden adlandırılması gerektiğini belirten `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="ac841-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="ac841-121">Daha karmaşık işleme senaryolarda, ikinci parametresinin <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi yetkilendirme altyapı geri her sonraki çağrı sırasında geçer bir durum değişkeninin depolamak için kullanılan <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> belirli bir değerlendirme için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ac841-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="ac841-122">Özel yetkilendirme ilkesi yapılandırma yoluyla belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ac841-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="ac841-123">İçinde özel yetkilendirme ilkesi türünü belirtin `policyType` özniteliğini `add` öğesinde `authorizationPolicies` öğesinde `serviceAuthorization` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ac841-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="ac841-124">Özel yetkilendirme ilkesi kod aracılığıyla belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ac841-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="ac841-125">Oluşturma bir <xref:System.Collections.Generic.List%601> , <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ac841-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="ac841-126">Özel yetkilendirme ilkesi örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac841-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="ac841-127">Yetkilendirme ilkesi örneği listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac841-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="ac841-128">Her bir özel yetkilendirme ilkesi için 2 ve 3. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="ac841-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="ac841-129">Listeye salt okunur bir sürümünü atamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ac841-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="ac841-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac841-130">Example</span></span>  
 <span data-ttu-id="ac841-131">Aşağıdaki örnek, bir tam gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ac841-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ac841-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac841-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="ac841-133">Nasıl yapılır: Talepleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ac841-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [<span data-ttu-id="ac841-134">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac841-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="ac841-135">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="ac841-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
