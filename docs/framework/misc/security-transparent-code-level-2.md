---
title: "Güvenliği Saydam Kod, 2. Düzey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bd4ee6c43b5089c45789b4f22326e17ec2218c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="dc830-102">Güvenliği Saydam Kod, 2. Düzey</span><span class="sxs-lookup"><span data-stu-id="dc830-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="dc830-103">Düzey 2 saydamlık sunulmuştur [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc830-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="dc830-104">Bu modelin üç tenets şunlardır: saydam kod, güvenlik açısından güvenli-kritik kod ve güvenlik açısından kritik kod.</span><span class="sxs-lookup"><span data-stu-id="dc830-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="dc830-105">Saydam kod, tam güven çalışan kodu da dahil olmak üzere diğer saydam kod veya yalnızca güvenlik açısından güvenli-kritik kod çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="dc830-106">Yalnızca, (varsa) etki alanının kısmi güven izni tarafından izin verilen eylemleri de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc830-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="dc830-107">Saydam kod aşağıdakileri yapamazsınız:</span><span class="sxs-lookup"><span data-stu-id="dc830-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="dc830-108">Gerçekleştirmek bir <xref:System.Security.CodeAccessPermission.Assert%2A> veya ayrıcalık yükseltme.</span><span class="sxs-lookup"><span data-stu-id="dc830-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="dc830-109">Güvenli olmayan veya doğrulanamayan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="dc830-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="dc830-110">Doğrudan kritik kod çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="dc830-111">Yerel kod çağrısı veya sahip code <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc830-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="dc830-112">Tarafından korunan bir üye çağırın bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="dc830-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="dc830-113">Kritik türlerinden devralır.</span><span class="sxs-lookup"><span data-stu-id="dc830-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="dc830-114">Ayrıca, saydam yöntemler kritik sanal yöntemleri geçersiz kılmak veya kritik arabirim yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="dc830-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="dc830-115">Güvenli kritik kodu tam olarak güvenilmeyen ancak saydam kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="dc830-116">Tam güven kodunun sınırlı bir yüzey alanını gösterir; doğruluk ve güvenlik Doğrulamalar güvenli kritik kodda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="dc830-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="dc830-117">Güvenlik açısından kritik kod herhangi bir kod çağırabilir ve tam olarak güvenilmeyen ancak tarafından saydam kod çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="dc830-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="dc830-118">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="dc830-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="dc830-119">Kullanım örnekleri ve davranışları</span><span class="sxs-lookup"><span data-stu-id="dc830-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="dc830-120">Desenler geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="dc830-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="dc830-121">Devralma kuralları</span><span class="sxs-lookup"><span data-stu-id="dc830-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="dc830-122">Ek bilgi ve kurallar</span><span class="sxs-lookup"><span data-stu-id="dc830-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="dc830-123">Kullanım Örnekleri ve Davranışlar</span><span class="sxs-lookup"><span data-stu-id="dc830-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="dc830-124">Belirtmek için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] kurallarını (Düzey 2 saydamlık), bir derleme için aşağıdaki ek açıklama kullanın:</span><span class="sxs-lookup"><span data-stu-id="dc830-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="dc830-125">.NET Framework 2.0 kurallara (düzey 1 saydamlık) kilitlemek için aşağıdaki ek açıklama kullanın:</span><span class="sxs-lookup"><span data-stu-id="dc830-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="dc830-126">Bir derlemeyi açıklama değil eklerseniz [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] kuralları, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc830-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="dc830-127">Ancak, önerilen en iyi uygulama olarak kullanmaktır <xref:System.Security.SecurityRulesAttribute> bağlı olarak varsayılan özniteliği yerine.</span><span class="sxs-lookup"><span data-stu-id="dc830-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="dc830-128">Derleme genelinde ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="dc830-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="dc830-129">Derleme düzeyindeki öznitelikler kullanımına aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="dc830-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="dc830-130">Hiçbir öznitelik: öznitelik belirtmezseniz, çalışma zamanı tüm kod güvenlik kritik, güvenlik açısından kritik olan bir devralma kuralı burada ihlal dışında olarak yorumlar (örneğin, geçersiz kılma veya saydam bir uygulama, sanal veya arabirim yöntemi ).</span><span class="sxs-lookup"><span data-stu-id="dc830-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="dc830-131">Bu gibi durumlarda yöntemler güvenli önemlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="dc830-132">Hiçbir öznitelik belirtilmesi saydamlık kuralları sizin için belirlemek ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="dc830-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   <span data-ttu-id="dc830-133">`SecurityTransparent`: Tüm kod saydamdır; Tüm derleme ayrıcalıklı veya güvenli olmayan yapmaz.</span><span class="sxs-lookup"><span data-stu-id="dc830-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   <span data-ttu-id="dc830-134">`SecurityCritical`: Bu derlemedeki türleri tarafından sunulan tüm kod önemlidir; diğer tüm kod saydamdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="dc830-135">Bu senaryoda, tüm öznitelikleri değil belirtme benzer; Ancak, ortak dil çalışma zamanı saydamlık kuralları otomatik olarak belirlemez.</span><span class="sxs-lookup"><span data-stu-id="dc830-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="dc830-136">Örneğin, bir sanal veya soyut yöntemi geçersiz kılma veya arabirim yöntemi, varsayılan olarak uygulamak, bu yöntem saydamdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="dc830-137">Açıkça yöntemi olarak ek açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`; Aksi halde, bir <xref:System.TypeLoadException> yükleme zamanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dc830-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="dc830-138">Bu kural, ayrıca hem temel sınıfını hem de türetilmiş bir sınıf aynı bütünleştirilmiş kodda olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   <span data-ttu-id="dc830-139">`AllowPartiallyTrustedCallers`(Düzey 2 yalnızca): tüm varsayılanları saydam kod.</span><span class="sxs-lookup"><span data-stu-id="dc830-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="dc830-140">Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="dc830-141">Aşağıdaki tabloda, Düzey 2 Düzey 1 için derleme düzeyi davranışı karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="dc830-141">The following table compares the assembly level behavior for Level 2 with Level 1 .</span></span>  
  
|<span data-ttu-id="dc830-142">Derleme özniteliği</span><span class="sxs-lookup"><span data-stu-id="dc830-142">Assembly attribute</span></span>|<span data-ttu-id="dc830-143">Düzey 2</span><span class="sxs-lookup"><span data-stu-id="dc830-143">Level 2</span></span>|<span data-ttu-id="dc830-144">Düzey 1</span><span class="sxs-lookup"><span data-stu-id="dc830-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="dc830-145">Kısmen güvenilir bir derleme üzerinde özniteliği yok</span><span class="sxs-lookup"><span data-stu-id="dc830-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="dc830-146">Türleri ve üyeleri saydam varsayılan olarak, ancak güvenlik açısından kritik ya da güvenlik açısından güvenli-kritik olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="dc830-147">Tüm türleri ve üyeleri saydamdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="dc830-148">Bir öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="dc830-148">No attribute</span></span>|<span data-ttu-id="dc830-149">Hiçbir öznitelik belirtilmesi saydamlık kuralları sizin için belirlemek ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="dc830-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="dc830-150">Tüm türleri ve üyeleri güvenlik-burada güvenlik açısından kritik olan bir devralma kuralı ihlal dışında önemlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="dc830-151">Tam olarak güvenilir bir derleme üzerinde (genel derleme önbelleğinde veya tam güvende olarak tanımlanan `AppDomain`) tüm türleri saydam ve tüm güvenlik açısından güvenli-kritik üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="dc830-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="dc830-152">Tüm türleri ve üyeleri saydamdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-152">All types and members are transparent.</span></span>|<span data-ttu-id="dc830-153">Tüm türleri ve üyeleri saydamdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="dc830-154">Yok.</span><span class="sxs-lookup"><span data-stu-id="dc830-154">Not applicable.</span></span>|<span data-ttu-id="dc830-155">Tüm türleri ve üyeleri güvenlik açısından kritik.</span><span class="sxs-lookup"><span data-stu-id="dc830-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="dc830-156">Bu derlemedeki türleri tarafından tanıtılan tüm kod önemlidir; diğer tüm kod saydamdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="dc830-157">Bir sanal veya soyut yöntemi geçersiz kılma veya bir arabirim yöntemini uygulayın, yöntemi olarak açıkça açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="dc830-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="dc830-158">Tüm Varsayılanları saydam kod.</span><span class="sxs-lookup"><span data-stu-id="dc830-158">All code defaults to transparent.</span></span> <span data-ttu-id="dc830-159">Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="dc830-160">Tür ve Üye Ek Açıklaması</span><span class="sxs-lookup"><span data-stu-id="dc830-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="dc830-161">Bir türe uygulanan güvenlik özniteliklerini türü tarafından sunulan üyeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="dc830-162">Ancak, bunlar için sanal uygulamayın veya soyut taban sınıf veya arabirim uygulamaları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dc830-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="dc830-163">Tür ve üye düzeyinde öznitelikleri kullanımına aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="dc830-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   <span data-ttu-id="dc830-164">`SecurityCritical`: Tür veya üye kritik öneme sahiptir ve yalnızca tam güven kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="dc830-165">Güvenlik açısından kritik tür tarafından sunulan yöntemleri önemlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="dc830-166">Temel sınıflar veya arabirimlerini sunulan ve geçersiz veya bir güvenlik açısından kritik sınıfta uygulanan sanal ve soyut yöntemleri, varsayılan olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="dc830-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="dc830-167">Bunlar ya da tanımlanmalıdır `SecuritySafeCritical` veya `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="dc830-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   <span data-ttu-id="dc830-168">`SecuritySafeCritical`: Tür veya üye güvenli kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dc830-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="dc830-169">Ancak, tür veya üye saydam (kısmen güvenilen) koddan çağrılan ve diğer kritik kod özelliğine sahip.</span><span class="sxs-lookup"><span data-stu-id="dc830-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="dc830-170">Kod için güvenlik denetlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc830-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="dc830-171">Başa dön</span><span class="sxs-lookup"><span data-stu-id="dc830-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="dc830-172">Desenleri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="dc830-172">Override Patterns</span></span>  
 <span data-ttu-id="dc830-173">Aşağıdaki tabloda, Düzey 2 saydamlık için izin verilen yöntemi geçersiz kılmaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc830-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="dc830-174">Temel sanal/arabirim üye</span><span class="sxs-lookup"><span data-stu-id="dc830-174">Base virtual/interface member</span></span>|<span data-ttu-id="dc830-175">Geçersiz kılma/arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc830-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="dc830-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="dc830-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="dc830-177">Devralma Kuralları</span><span class="sxs-lookup"><span data-stu-id="dc830-177">Inheritance Rules</span></span>  
 <span data-ttu-id="dc830-178">Bu bölümde, aşağıdaki sırayla atanan `Transparent`, `Critical`, ve `SafeCritical` kod tabanlı erişim ve özellikleri:</span><span class="sxs-lookup"><span data-stu-id="dc830-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="dc830-179">Türler için kuralları: soldan sağa giderek, erişim daha kısıtlayıcı olur.</span><span class="sxs-lookup"><span data-stu-id="dc830-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="dc830-180">Türetilmiş türler en az temel tür olarak olabildiğince kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc830-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="dc830-181">Kuralları yöntemleri için: türetilmiş yöntemleri temel yöntemden erişilebilirlik değiştiremiyor.</span><span class="sxs-lookup"><span data-stu-id="dc830-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="dc830-182">İçin varsayılan davranış, değil açıklama eklenen tüm türetilmiş yöntemlerdir `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="dc830-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="dc830-183">Kritik türleri türevleri geçersiz kılınan yöntemi açıkça olarak açıklama eklenmemiş erişilirse durum için bir özel duruma neden `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="dc830-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="dc830-184">Aşağıdaki tabloda izin verilen türü devralma desenleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="dc830-185">Taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="dc830-185">Base class</span></span>|<span data-ttu-id="dc830-186">Türetilmiş sınıf olabilir</span><span class="sxs-lookup"><span data-stu-id="dc830-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="dc830-187">Aşağıdaki tabloda izin verilmeyen türü devralma desenleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="dc830-188">Taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="dc830-188">Base class</span></span>|<span data-ttu-id="dc830-189">Türetilmiş sınıf olamaz</span><span class="sxs-lookup"><span data-stu-id="dc830-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="dc830-190">Aşağıdaki tabloda izin verilen yöntemi devralma desenleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="dc830-191">Base yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc830-191">Base method</span></span>|<span data-ttu-id="dc830-192">Türetilen bir yöntem olabilir</span><span class="sxs-lookup"><span data-stu-id="dc830-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="dc830-193">Aşağıdaki tabloda izin verilmeyen yöntemi devralma desenleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="dc830-194">Base yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc830-194">Base method</span></span>|<span data-ttu-id="dc830-195">Türetilen yöntem olamaz</span><span class="sxs-lookup"><span data-stu-id="dc830-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="dc830-196">Bu devralma kurallar, Düzey 2 türleri ve üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="dc830-197">Düzey 1 derlemelerindeki Düzey 2 güvenlik kritik türleri ve üyeleri devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc830-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="dc830-198">Bu nedenle, Düzey 2 türleri ve üyeleri düzey 1 notlar için ayrı devralma taleplerini olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc830-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="dc830-199">Başa dön</span><span class="sxs-lookup"><span data-stu-id="dc830-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="dc830-200">Ek Bilgiler ve Kurallar</span><span class="sxs-lookup"><span data-stu-id="dc830-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="dc830-201">LinkDemand Desteği</span><span class="sxs-lookup"><span data-stu-id="dc830-201">LinkDemand Support</span></span>  
 <span data-ttu-id="dc830-202">Düzey 2 saydamlık modeli değiştirir <xref:System.Security.Permissions.SecurityAction.LinkDemand> ile <xref:System.Security.SecurityCriticalAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc830-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="dc830-203">Eski (düzey 1) kodda bir <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik olarak işlem görür bir <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="dc830-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="dc830-204">Yansıma</span><span class="sxs-lookup"><span data-stu-id="dc830-204">Reflection</span></span>  
 <span data-ttu-id="dc830-205">(Yalnızca bir özel yöntem veya alan başlattığınız sanki) kritik yönteminin çağrılması veya kritik bir alanın okunması tam güven için talep tetikler.</span><span class="sxs-lookup"><span data-stu-id="dc830-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="dc830-206">Bu nedenle, kısmi güven kodunun edilemez ise tam güven kod kritik yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc830-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="dc830-207">Aşağıdaki özellikler için eklenene <xref:System.Reflection> türü, yöntemi veya alanı olup olmadığını belirlemek için ad alanı `SecurityCritical`, `SecuritySafeCritical`, veya `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ve <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc830-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="dc830-208">Öznitelik varlığını denetimi yerine yansıma kullanarak saydamlık belirlemek için bu özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="dc830-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="dc830-209">Saydamlık kuralları karmaşıktır ve özniteliğini denetimi yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="dc830-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc830-210">A `SafeCritical` yöntemi döndürür `true` her ikisi için de <xref:System.Type.IsSecurityCritical%2A> ve <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, çünkü `SafeCritical` (kritik kod aynı özelliklerine sahiptir, ancak saydam koddan çağrılabilir) gerçekten önemlidir.</span><span class="sxs-lookup"><span data-stu-id="dc830-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="dc830-211">Dinamik yöntemler bağlı olan modüller saydamlığını devralır; (bir türe bağlıysa) türü saydamlığını devralmaz.</span><span class="sxs-lookup"><span data-stu-id="dc830-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="dc830-212">Tam Güven İçinde Doğrulamayı Atlama</span><span class="sxs-lookup"><span data-stu-id="dc830-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="dc830-213">Ayarlayarak tam güvenilir saydam derlemeler için doğrulama atlayabilirsiniz <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> özelliğine `true` içinde <xref:System.Security.SecurityRulesAttribute> özniteliği:</span><span class="sxs-lookup"><span data-stu-id="dc830-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="dc830-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Özelliği `false` varsayılan olarak, bu nedenle özelliği ayarlanmalıdır `true` doğrulaması atlanacak.</span><span class="sxs-lookup"><span data-stu-id="dc830-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="dc830-215">Bu, yalnızca en iyi duruma getirme amacıyla yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc830-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="dc830-216">Derlemedeki saydam kod kullanılarak doğrulanabilir olduğundan emin olmanız gerekir `transparent` seçeneğini [PEVerify aracı](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="dc830-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc830-217">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc830-217">See Also</span></span>  
 [<span data-ttu-id="dc830-218">Güvenliği saydam kod, düzey 1</span><span class="sxs-lookup"><span data-stu-id="dc830-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [<span data-ttu-id="dc830-219">Güvenlik değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="dc830-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
