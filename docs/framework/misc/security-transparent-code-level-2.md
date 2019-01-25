---
title: Güvenliği Saydam Kod, 2. Düzey
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8425b294328d4fc7546a372b329d8fa834a088d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567028"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="d2c4f-102">Güvenliği Saydam Kod, 2. Düzey</span><span class="sxs-lookup"><span data-stu-id="d2c4f-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="d2c4f-103">Düzey 2 saydamlık öğesinde tanıtılmıştır [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2c4f-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="d2c4f-104">Bu modelin üç İlkesi saydam kod güvenlik güvenli kritik kod ve güvenlik açısından kritik kod ' dir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="d2c4f-105">Saydam kod tam güven çalışan kodu da dahil olmak üzere, diğer saydam kod veya yalnızca güvenlik-güvenli-kritik kodu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="d2c4f-106">Yalnızca, (varsa) ayarlayın etki alanının kısmi güven izni tarafından izin verilen eylemleri de gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="d2c4f-107">Saydam kod aşağıdaki işlemleri yapamaz:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="d2c4f-108">Gerçekleştirmek bir <xref:System.Security.CodeAccessPermission.Assert%2A> veya ayrıcalık yükseltme.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="d2c4f-109">Güvenli olmayan veya doğrulanamaz kod içerir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="d2c4f-110">Doğrudan kritik kodu çağırın.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="d2c4f-111">Yerel koda çağrı yapma veya kod <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="d2c4f-112">Tarafından korunan üyeyi çağırın bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="d2c4f-113">Kritik türlerden devral</span><span class="sxs-lookup"><span data-stu-id="d2c4f-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="d2c4f-114">Ayrıca, saydam yöntemleri kritik sanal yöntemleri geçersiz kılmaz veya kritik arabirim yöntemlerini uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="d2c4f-115">Güvenli kritik kod, tam olarak güvenilirdir ancak saydam kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="d2c4f-116">Bu, tam güven kodu sınırlı yüzey alanı sunar; düzeltmeler ve güvenlik doğrulamaları güvenli kritik kodda olur.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="d2c4f-117">Güvenlik açısından kritik kod, herhangi bir kodu çağırabilir ve tam olarak güvenilirdir ancak saydam kod tarafından çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="d2c4f-118">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d2c4f-119">Kullanım örnekleri ve davranışlar</span><span class="sxs-lookup"><span data-stu-id="d2c4f-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="d2c4f-120">Desenleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="d2c4f-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="d2c4f-121">Devralma kuralları</span><span class="sxs-lookup"><span data-stu-id="d2c4f-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="d2c4f-122">Ek bilgiler ve kurallar</span><span class="sxs-lookup"><span data-stu-id="d2c4f-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="d2c4f-123">Kullanım Örnekleri ve Davranışlar</span><span class="sxs-lookup"><span data-stu-id="d2c4f-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="d2c4f-124">Belirtmek için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (Düzey 2 saydamlık) kuralları, bir derleme için aşağıdaki ek açıklama kullanın:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="d2c4f-125">.NET Framework 2.0 kuralları (düzey 1 saydamlık) kilitlemek için aşağıdaki ek açıklama kullanın:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="d2c4f-126">Bir derlemeyi not ekleyemezsiniz, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] kuralları, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="d2c4f-127">Ancak, önerilen en iyi kullanmaktır <xref:System.Security.SecurityRulesAttribute> bağlı olarak varsayılan öznitelik yerine.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="d2c4f-128">Derleme genelinde ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="d2c4f-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="d2c4f-129">Öznitelikleri derleme düzeyinde kullanımı için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="d2c4f-130">Hiçbir öznitelik: Herhangi bir özniteliği belirtmezseniz, çalışma zamanı, tüm kod güvenlik kritik, burada güvenlik açısından kritik olan bir devralma kuralı ihlal dışında olarak yorumlar. (örneğin, geçersiz kılma veya saydam bir uygulama sanal ya da arabirim yöntemi).</span><span class="sxs-lookup"><span data-stu-id="d2c4f-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="d2c4f-131">Bu gibi durumlarda, güvenli kritik yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="d2c4f-132">Hiçbir öznitelik belirtmemeye sizin için saydamlık kuralları belirlemek ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   <span data-ttu-id="d2c4f-133">`SecurityTransparent`: Tüm kod saydamdır; Tüm derleme ayrıcalıklı veya güvenli olmayan hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   <span data-ttu-id="d2c4f-134">`SecurityCritical`: Bu derlemedeki türleri tarafından tanıtılan tüm kod büyük/küçük harf önemlidir; diğer tüm kod saydamdır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="d2c4f-135">Bu senaryo, herhangi bir özniteliği değil belirtme benzer. Ancak, ortak dil çalışma zamanı, saydamlık kuralları otomatik olarak belirlemez.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="d2c4f-136">Örneğin, bu yöntem sanal veya soyut bir yöntemi geçersiz kılın veya varsayılan bir arabirim yöntemini uygulamak, saydamdır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="d2c4f-137">Açıkça yöntemi olarak ek açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`; Aksi takdirde bir <xref:System.TypeLoadException> yükleme zamanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="d2c4f-138">Bu kural, ayrıca temel sınıfını hem türetilen sınıfın aynı bütünleştirilmiş kodda olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   <span data-ttu-id="d2c4f-139">`AllowPartiallyTrustedCallers` (Düzey 2 yalnızca): Tüm Varsayılanları saydam kod.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="d2c4f-140">Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="d2c4f-141">Aşağıdaki tabloda, düzey 1 Düzey 2 için derleme düzeyi davranışı karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>  
  
|<span data-ttu-id="d2c4f-142">Bütünleştirilmiş kod özniteliği</span><span class="sxs-lookup"><span data-stu-id="d2c4f-142">Assembly attribute</span></span>|<span data-ttu-id="d2c4f-143">Düzey 2</span><span class="sxs-lookup"><span data-stu-id="d2c4f-143">Level 2</span></span>|<span data-ttu-id="d2c4f-144">Düzey 1</span><span class="sxs-lookup"><span data-stu-id="d2c4f-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="d2c4f-145">Kısmen güvenilen bir derleme üzerinde herhangi bir öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="d2c4f-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="d2c4f-146">Türleri ve üyeleri varsayılan olarak saydam olan, ancak güvenlik açısından kritik veya güvenlik güvenli kritik olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="d2c4f-147">Tüm türler ve üyeler görünmez.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="d2c4f-148">Bir öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="d2c4f-148">No attribute</span></span>|<span data-ttu-id="d2c4f-149">Hiçbir öznitelik belirtmemeye sizin için saydamlık kuralları belirlemek ortak dil çalışma zamanı neden olur.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="d2c4f-150">Tüm türleri ve üyeleri güvenlik-burada güvenlik açısından kritik olan bir devralma kuralı ihlal ediyor dışında önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="d2c4f-151">Tam olarak güvenilen bir derleme üzerinde (genel derleme önbelleğinde veya tam güven olarak tanımlanan `AppDomain`) tüm türleri şeffaftır ve tüm üyeleri güvenlik-güvenli-kritik.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="d2c4f-152">Tüm türler ve üyeler görünmez.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-152">All types and members are transparent.</span></span>|<span data-ttu-id="d2c4f-153">Tüm türler ve üyeler görünmez.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="d2c4f-154">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-154">Not applicable.</span></span>|<span data-ttu-id="d2c4f-155">Tüm türleri ve üyeleri güvenlik kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="d2c4f-156">Bu derlemedeki türleri tarafından tanıtılan tüm kod büyük/küçük harf önemlidir; diğer tüm kod saydamdır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="d2c4f-157">Sanal veya soyut bir yöntemi geçersiz kılmak veya bir arabirimin yöntemini uygulayan yöntemi olarak açıkça açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="d2c4f-158">Tüm Varsayılanları saydam kod.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-158">All code defaults to transparent.</span></span> <span data-ttu-id="d2c4f-159">Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="d2c4f-160">Tür ve Üye Ek Açıklaması</span><span class="sxs-lookup"><span data-stu-id="d2c4f-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="d2c4f-161">Bir türe uygulanan güvenlik öznitelikleri türü tarafından sunulan üyeler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="d2c4f-162">Ancak, bunlar için sanal uygulanmaz veya soyut temel sınıf veya arabirim uygulamaları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="d2c4f-163">Tür ve üye düzeyinde öznitelikler kullanımı için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   <span data-ttu-id="d2c4f-164">`SecurityCritical`: Türe veya üyeye kritik öneme sahiptir ve yalnızca tam güvenilir kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="d2c4f-165">Güvenlik açısından kritik bir tür içinde sunulan yöntemleri kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d2c4f-166">Temel sınıflar ya da arabirimleri, dahil edilen ve geçersiz kılınmış veya uygulanan güvenlik açısından kritik bir sınıfta sanal ve Özet yöntemleri tarafından varsayılan olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="d2c4f-167">Bunlar olarak tanımlanmalıdır `SecuritySafeCritical` veya `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   <span data-ttu-id="d2c4f-168">`SecuritySafeCritical`: Türe veya üyeye güvenli kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="d2c4f-169">Ancak, türe veya üyeye (kısmen güvenilen) saydam koddan çağrılabilir ve diğer kritik kod özelliğine sahip.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="d2c4f-170">Kod için güvenlik denetlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="d2c4f-171">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d2c4f-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="d2c4f-172">Desenleri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="d2c4f-172">Override Patterns</span></span>  
 <span data-ttu-id="d2c4f-173">Aşağıdaki tabloda, Düzey 2 saydamlık için izin verilen yöntemi geçersiz kılmaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="d2c4f-174">Temel sanal/arabirim üyesi</span><span class="sxs-lookup"><span data-stu-id="d2c4f-174">Base virtual/interface member</span></span>|<span data-ttu-id="d2c4f-175">Geçersiz kılma/arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2c4f-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="d2c4f-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d2c4f-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="d2c4f-177">Devralma Kuralları</span><span class="sxs-lookup"><span data-stu-id="d2c4f-177">Inheritance Rules</span></span>  
 <span data-ttu-id="d2c4f-178">Bu bölümde, aşağıdaki sırayla atanan `Transparent`, `Critical`, ve `SafeCritical` kod tabanlı erişim ve özellikleri:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="d2c4f-179">Kural türü için: Soldan sağa doğru giden, erişim daha kısıtlayıcı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="d2c4f-180">Türetilen türlerin, en az bir temel tür olarak olabildiğince kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="d2c4f-181">Kuralları yöntemleri için: Türetilmiş yöntemleri erişilebilirlik taban yöntemden değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="d2c4f-182">Varsayılan davranışı için değil açıklamalı olan tüm türetilmiş yöntemlerdir `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="d2c4f-183">Kritik türler CIM'in neden bir özel geçersiz kılınan yöntemi açıkça olarak değil eklenmişse durum `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="d2c4f-184">Aşağıdaki tabloda, izin verilen tür devralma desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="d2c4f-185">Temel sınıf</span><span class="sxs-lookup"><span data-stu-id="d2c4f-185">Base class</span></span>|<span data-ttu-id="d2c4f-186">Türetilmiş sınıf olabilir</span><span class="sxs-lookup"><span data-stu-id="d2c4f-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="d2c4f-187">Aşağıdaki tabloda, izin verilmeyen türü devralma desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="d2c4f-188">Temel sınıf</span><span class="sxs-lookup"><span data-stu-id="d2c4f-188">Base class</span></span>|<span data-ttu-id="d2c4f-189">Türetilmiş sınıf olamaz</span><span class="sxs-lookup"><span data-stu-id="d2c4f-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="d2c4f-190">Aşağıdaki tabloda, izin verilen yöntemi devralma desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="d2c4f-191">Taban yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2c4f-191">Base method</span></span>|<span data-ttu-id="d2c4f-192">Türetilen bir yöntem olabilir</span><span class="sxs-lookup"><span data-stu-id="d2c4f-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="d2c4f-193">Aşağıdaki tabloda, izin verilmeyen yöntemi devralma desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="d2c4f-194">Taban yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2c4f-194">Base method</span></span>|<span data-ttu-id="d2c4f-195">Türetilmiş yöntemi olamaz</span><span class="sxs-lookup"><span data-stu-id="d2c4f-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="d2c4f-196">Bu devralma kuralları, Düzey 2 türler ve üyeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="d2c4f-197">Düzey 1 bütünleştirilmiş kodlar içindeki türleri, Düzey 2 güvenlik kritik türleri ve üyeleri devralabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="d2c4f-198">Bu nedenle, Düzey 2 türler ve üyeler için düzey 1 devralanlar ayrı devralma taleplerini olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="d2c4f-199">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d2c4f-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="d2c4f-200">Ek Bilgiler ve Kurallar</span><span class="sxs-lookup"><span data-stu-id="d2c4f-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="d2c4f-201">LinkDemand Desteği</span><span class="sxs-lookup"><span data-stu-id="d2c4f-201">LinkDemand Support</span></span>  
 <span data-ttu-id="d2c4f-202">Düzey 2 saydamlık modelinin yerini <xref:System.Security.Permissions.SecurityAction.LinkDemand> ile <xref:System.Security.SecurityCriticalAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="d2c4f-203">Eski (düzey 1) kodda, bir <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik olarak kabul edilir bir <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="d2c4f-204">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d2c4f-204">Reflection</span></span>  
 <span data-ttu-id="d2c4f-205">(Yalnızca özel metodu nebo pole başlattığınız yokmuş gibi) isteğe bağlı tam güven için kritik bir yöntem çağırma veya bir kritik alanının okunmasını tetikler.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="d2c4f-206">Bu nedenle, kısmi güven kodu olamaz ancak tam güven kodu kritik bir yöntem çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="d2c4f-207">Aşağıdaki özellikler eklenmiştir <xref:System.Reflection> türü, yöntemi veya alan olup olmadığını belirlemek için ad alanı `SecurityCritical`, `SecuritySafeCritical`, veya `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ve <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="d2c4f-208">Öznitelik varlığını denetleme yerine yansıma kullanarak saydamlığı belirlemek için bu özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="d2c4f-209">Saydamlık kuralları karmaşıktır ve denetimi özniteliği için yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2c4f-210">A `SafeCritical` yöntemi döndürür `true` hem <xref:System.Type.IsSecurityCritical%2A> ve <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, çünkü `SafeCritical` (kritik kod ile aynı özellikleri vardır, ancak saydam koddan çağrılabilir) gerçekten de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="d2c4f-211">Dinamik yöntemler için eklenen modülleri saydamlığını devralır; (bir türe ekliyse) türü saydamlığını devralmaz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="d2c4f-212">Tam Güven İçinde Doğrulamayı Atlama</span><span class="sxs-lookup"><span data-stu-id="d2c4f-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="d2c4f-213">Doğrulama için saydam tamamen güvenilir derlemelerinin ayarlayarak atlayabilirsiniz <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> özelliğini `true` içinde <xref:System.Security.SecurityRulesAttribute> özniteliği:</span><span class="sxs-lookup"><span data-stu-id="d2c4f-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="d2c4f-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Özelliği `false` varsayılan olarak, bu nedenle özelliği ayarlanmalıdır `true` doğrulamayı atlamasına.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="d2c4f-215">Bu, yalnızca en iyi duruma getirme amacıyla yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="d2c4f-216">Saydam kod derleme içindeki kullanılarak doğrulanabilir olduğundan emin olmanız gerekir `transparent` seçeneğini [PEVerify aracı](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d2c4f-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c4f-217">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-217">See also</span></span>
- [<span data-ttu-id="d2c4f-218">Güvenliği saydam kod, düzey 1</span><span class="sxs-lookup"><span data-stu-id="d2c4f-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [<span data-ttu-id="d2c4f-219">Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="d2c4f-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
