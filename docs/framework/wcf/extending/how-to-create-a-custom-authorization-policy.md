---
title: "Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma"
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
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1af5e2cbf7c124e490fea04deadd1afffcde5cbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="aa783-102">Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa783-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="aa783-103">Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] talep tabanlı yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="aa783-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a claim-based authorization model.</span></span> <span data-ttu-id="aa783-104">Talep belirteçlerinden ayıklanan, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenen ve içine yerleştirilen bir <xref:System.IdentityModel.Policy.AuthorizationContext> , sonra incelenmesi yetkilendirme kararları vermek için.</span><span class="sxs-lookup"><span data-stu-id="aa783-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="aa783-105">Özel bir ilke, uygulama tarafından beklenen talep gelen belirteçleri talepleri dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa783-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="aa783-106">Bu şekilde, uygulama katmanı tarafından sunulan farklı taleplerdeki ayrıntıları yalıtılmış farklı belirteç türleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler.</span><span class="sxs-lookup"><span data-stu-id="aa783-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports.</span></span> <span data-ttu-id="aa783-107">Bu konu, özel yetkilendirme ilkesi uygulama ve hizmet tarafından kullanılan ilkeleri koleksiyonunu o ilke eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa783-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="aa783-108">Özel yetkilendirme ilkesi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="aa783-108">To implement a custom authorization policy</span></span>  
  
1.  <span data-ttu-id="aa783-109">Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="aa783-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="aa783-110">Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> özelliği erişildiğinde sınıfa ilişkin oluşturucuda benzersiz bir dize oluşturma ve bu dizeyi özelliği.</span><span class="sxs-lookup"><span data-stu-id="aa783-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3.  <span data-ttu-id="aa783-111">Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> döndürerek özelliği bir <xref:System.IdentityModel.Claims.ClaimSet> İlkesi veren temsil eden.</span><span class="sxs-lookup"><span data-stu-id="aa783-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="aa783-112">Bunun bir `ClaimSet` uygulama veya yerleşik bir temsil eden `ClaimSet` (örneğin, `ClaimSet` statik tarafından döndürülen <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aa783-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4.  <span data-ttu-id="aa783-113">Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> aşağıdaki yordamda açıklandığı gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aa783-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="aa783-114">Evaluate yöntemi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="aa783-114">To implement the Evaluate method</span></span>  
  
1.  <span data-ttu-id="aa783-115">İki parametre bu yönteme geçirilen: örneği <xref:System.IdentityModel.Policy.EvaluationContext> sınıf ve nesne başvurusu.</span><span class="sxs-lookup"><span data-stu-id="aa783-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2.  <span data-ttu-id="aa783-116">Özel yetkilendirme ilkesi eklerse <xref:System.IdentityModel.Claims.ClaimSet> geçerli içeriğini dikkate almaksızın örnekleri <xref:System.IdentityModel.Policy.EvaluationContext>, her ekleyin `ClaimSet` çağırarak <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve return `true` gelen <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aa783-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="aa783-117">Döndürme `true` yetkilendirme altyapı yetkilendirme ilkesi çalışmasını yürüttü ve yeniden çağrılması gerekmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa783-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3.  <span data-ttu-id="aa783-118">Yalnızca belirli talepler zaten varsa özel yetkilendirme ilkesi talep kümelerinin eklerse `EvaluationContext`, sonra bu talepleri için inceleyerek bakın `ClaimSet` tarafından döndürülen örnek <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aa783-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="aa783-119">Talep varsa, ardından yeni talep ayarlar çağırarak ekleyin <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve kümeleridir eklenen, dönüş olması için daha fazla talep IF `true`, yetkilendirme ilkesini kendi çalışması tamamlandı yetkilendirme altyapısına belirten.</span><span class="sxs-lookup"><span data-stu-id="aa783-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="aa783-120">Talep mevcut değilse, dönüş `false`, diğer yetkilendirme ilkeleri daha eklerseniz, Yetkilendirme İlkesi'nin yeniden adlandırılması gerektiğini belirten talep kümeleri için `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="aa783-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4.  <span data-ttu-id="aa783-121">Daha karmaşık işleme senaryolarında, ikinci parametresi, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi yetkilendirme altyapı geri her sonraki çağrı sırasında geçecek bir durum değişkeninin depolamak için kullanılan <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> belirli bir değerlendirme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aa783-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="aa783-122">Özel yetkilendirme ilkesini yapılandırma yoluyla belirtmek için</span><span class="sxs-lookup"><span data-stu-id="aa783-122">To specify a custom authorization policy through configuration</span></span>  
  
1.  <span data-ttu-id="aa783-123">Özel yetkilendirme ilkesi türünü belirtin `policyType` özniteliğini `add` öğesinde `authorizationPolicies` öğesinde `serviceAuthorization` öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa783-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="aa783-124">Özel yetkilendirme ilkesi kodlarda belirtmek için</span><span class="sxs-lookup"><span data-stu-id="aa783-124">To specify a custom authorization policy through code</span></span>  
  
1.  <span data-ttu-id="aa783-125">Oluşturma bir <xref:System.Collections.Generic.List%601> , <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="aa783-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="aa783-126">Özel yetkilendirme ilkesi örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aa783-126">Create an instance of the custom authorization policy.</span></span>  
  
3.  <span data-ttu-id="aa783-127">Yetkilendirme ilkesi örneği listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa783-127">Add the authorization policy instance to the list.</span></span>  
  
4.  <span data-ttu-id="aa783-128">Her özel yetkilendirme ilkesi için 2 ve 3. adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="aa783-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5.  <span data-ttu-id="aa783-129">Listeye salt okunur bir sürümünü atamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aa783-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="aa783-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa783-130">Example</span></span>  
 <span data-ttu-id="aa783-131">Aşağıdaki örnek eksiksiz gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="aa783-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="aa783-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa783-132">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="aa783-133">Nasıl yapılır: Talepleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="aa783-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [<span data-ttu-id="aa783-134">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa783-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="aa783-135">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="aa783-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
