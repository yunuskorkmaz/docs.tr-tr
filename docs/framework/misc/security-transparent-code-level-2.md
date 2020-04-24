---
title: Güvenliği Saydam Kod, 2. Düzey
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645728"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="df67a-102">Güvenliği Saydam Kod, 2. Düzey</span><span class="sxs-lookup"><span data-stu-id="df67a-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="df67a-103">Düzey 2 saydamlığı .NET Framework 4'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="df67a-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="df67a-104">Bu modelin üç ilkeleri saydam kod, güvenlik açısından kritik kod ve güvenlik açısından kritik kodvardır.</span><span class="sxs-lookup"><span data-stu-id="df67a-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="df67a-105">Tam güven olarak çalışan kod da dahil olmak üzere saydam kod, diğer saydam kodu veya yalnızca güvenlik açısından kritik kodu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="df67a-106">Yalnızca etki alanının kısmi güven izin kümesi tarafından izin verilen eylemleri gerçekleştirebilir (varsa).</span><span class="sxs-lookup"><span data-stu-id="df67a-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="df67a-107">Saydam kod aşağıdakileri yapamaz:</span><span class="sxs-lookup"><span data-stu-id="df67a-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="df67a-108">Ayrıcalık <xref:System.Security.CodeAccessPermission.Assert%2A> veya yükseklik gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="df67a-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="df67a-109">Güvenli olmayan veya doğrulanamayan kod içerir.</span><span class="sxs-lookup"><span data-stu-id="df67a-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="df67a-110">Doğrudan kritik kodu arayın.</span><span class="sxs-lookup"><span data-stu-id="df67a-110">Directly call critical code.</span></span>

  - <span data-ttu-id="df67a-111">Öznitelik içeren <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> yerel kodu veya kodu arayın.</span><span class="sxs-lookup"><span data-stu-id="df67a-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="df67a-112">Bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>. tarafından korunan bir üyeyi arayın</span><span class="sxs-lookup"><span data-stu-id="df67a-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="df67a-113">Kritik türlerden devralma.</span><span class="sxs-lookup"><span data-stu-id="df67a-113">Inherit from critical types.</span></span>

  <span data-ttu-id="df67a-114">Buna ek olarak, saydam yöntemler kritik sanal yöntemleri geçersiz kılamaz veya kritik arabirim yöntemleri uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="df67a-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="df67a-115">Güvenli kritik kod tamamen güvenilirdir, ancak saydam kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="df67a-116">Tam güven kodunun sınırlı bir yüzey alanını ortaya çıkarır; doğruluk ve güvenlik doğrulamaları güvenli kritik kodda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="df67a-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="df67a-117">Güvenlik açısından kritik kod herhangi bir kodu arayabilir ve tam olarak güvenilirdir, ancak saydam kod la çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="df67a-118">Kullanım Örnekleri ve Davranışlar</span><span class="sxs-lookup"><span data-stu-id="df67a-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="df67a-119">.NET Framework 4 kurallarını (düzey 2 saydamlığı) belirtmek için, bir derleme için aşağıdaki ek açıklamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="df67a-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="df67a-120">.NET Framework 2.0 kurallarına (düzey 1 saydamlığı) kilitlemek için aşağıdaki ek açıklamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="df67a-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="df67a-121">Bir derlemeye açıklama yapmazsanız, .NET Framework 4 kuralları varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df67a-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="df67a-122">Ancak, önerilen en iyi yöntem <xref:System.Security.SecurityRulesAttribute> varsayılanbağlı yerine öznitelik kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="df67a-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="df67a-123">Montaj genelinde Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="df67a-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="df67a-124">Aşağıdaki kurallar derleme düzeyinde özniteliklerin kullanımı için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="df67a-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="df67a-125">Öznitelik belirtmezseniz: Herhangi bir öznitelik belirtmezseniz, çalışma zamanı, güvenlik açısından kritik olmanın bir devralma kuralını ihlal ettiği durumlar (örneğin, saydam bir sanal veya arabirim yöntemini geçersiz kıldığı veya uygularken) dışında tüm kodu güvenlik açısından kritik olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="df67a-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="df67a-126">Bu gibi durumlarda, yöntemler güvenli-kritik.</span><span class="sxs-lookup"><span data-stu-id="df67a-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="df67a-127">Hiçbir öznitelik belirtme, sizin için saydamlık kurallarını belirlemek için ortak dil çalışma süresineden olur.</span><span class="sxs-lookup"><span data-stu-id="df67a-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="df67a-128">`SecurityTransparent`: Tüm kod saydamdır; tüm derleme ayrıcalıklı veya güvensiz bir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="df67a-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="df67a-129">`SecurityCritical`: Bu derlemedeki türler tarafından getirilen tüm kodlar önemlidir; diğer tüm kod saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="df67a-130">Bu senaryo, herhangi bir öznitelik belirtmemeye benzer; ancak, ortak dil çalışma süresi saydamlık kurallarını otomatik olarak belirlemez.</span><span class="sxs-lookup"><span data-stu-id="df67a-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="df67a-131">Örneğin, sanal veya soyut bir yöntemi geçersiz kılarsanız veya varsayılan olarak bir arabirim yöntemi uygularsanız, bu yöntem saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="df67a-132">Yöntemi açıkça açıklama olarak veya; `SecurityCritical` `SecuritySafeCritical` aksi takdirde, yük zamanında bir atılmalıdır. <xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="df67a-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="df67a-133">Bu kural, hem taban sınıf hem de türemiş sınıf aynı derlemede olduğunda da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="df67a-134">`AllowPartiallyTrustedCallers`(yalnızca düzey 2): Tüm kod varsayılan olarak saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="df67a-135">Ancak, tek tek türleri ve üyeleri başka öznitelikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="df67a-136">Aşağıdaki tablo, Düzey 2 için derleme düzeyi davranışını Düzey 1 ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="df67a-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="df67a-137">Montaj özniteliği</span><span class="sxs-lookup"><span data-stu-id="df67a-137">Assembly attribute</span></span>|<span data-ttu-id="df67a-138">Düzey 2</span><span class="sxs-lookup"><span data-stu-id="df67a-138">Level 2</span></span>|<span data-ttu-id="df67a-139">Düzey 1</span><span class="sxs-lookup"><span data-stu-id="df67a-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="df67a-140">Kısmen güvenilen bir derlemede öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="df67a-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="df67a-141">Türler ve üyeler varsayılan olarak saydamdır, ancak güvenlik açısından kritik veya güvenlik açısından güvenli kritik olabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="df67a-142">Tüm tür ve üyeler saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="df67a-143">Öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="df67a-143">No attribute</span></span>|<span data-ttu-id="df67a-144">Hiçbir öznitelik belirtme, sizin için saydamlık kurallarını belirlemek için ortak dil çalışma süresineden olur.</span><span class="sxs-lookup"><span data-stu-id="df67a-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="df67a-145">Güvenlik açısından kritik olan ın bir devralma kuralını ihlal ettiği durumlar dışında, tüm türler ve üyeler güvenlik açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="df67a-146">Tam olarak güvenilen bir derlemede (genel montaj önbelleğinde veya tam güven olarak `AppDomain`tanımlanır) tüm türler saydamdır ve tüm üyeler güvenlik açısından kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="df67a-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="df67a-147">Tüm tür ve üyeler saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-147">All types and members are transparent.</span></span>|<span data-ttu-id="df67a-148">Tüm tür ve üyeler saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="df67a-149">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="df67a-149">Not applicable.</span></span>|<span data-ttu-id="df67a-150">Tüm türler ve üyeler güvenlik açısından kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="df67a-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="df67a-151">Bu derlemedeki türler tarafından tanıtılan tüm kod lar önemlidir; diğer tüm kod saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="df67a-152">Sanal veya soyut bir yöntemi geçersiz kılarsanız veya bir arabirim yöntemi uygularsanız, metodu açıkça `SecurityCritical` "veya `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="df67a-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="df67a-153">Tüm kod varsayılan olarak saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-153">All code defaults to transparent.</span></span> <span data-ttu-id="df67a-154">Ancak, tek tek türleri ve üyeleri başka öznitelikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="df67a-155">Tür ve Üye Ek Açıklaması</span><span class="sxs-lookup"><span data-stu-id="df67a-155">Type and Member Annotation</span></span>

<span data-ttu-id="df67a-156">Bir türe uygulanan güvenlik öznitelikleri, tür tarafından tanıtılan üyeler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="df67a-157">Ancak, temel sınıf veya arabirim uygulamalarının sanal veya soyut geçersiz kılmaları için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="df67a-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="df67a-158">Aşağıdaki kurallar, özniteliklerin tür ve üye düzeyinde kullanımı için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="df67a-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="df67a-159">`SecurityCritical`: Tür veya üye önemlidir ve yalnızca tam güven koduyla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="df67a-160">Güvenlik açısından kritik bir türde tanıtılan yöntemler önemlidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="df67a-161">Temel sınıflara veya arabirimlere getirilen ve güvenlik açısından kritik bir sınıfta geçersiz kılınan veya uygulanan sanal ve soyut yöntemler varsayılan olarak saydamdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="df67a-162">Ya da `SecuritySafeCritical` `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="df67a-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="df67a-163">`SecuritySafeCritical`: Türü veya üyesi güvenli kritik.</span><span class="sxs-lookup"><span data-stu-id="df67a-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="df67a-164">Ancak, tür veya üye saydam (kısmen güvenilen) koddan çağrılabilir ve diğer kritik kodlar kadar yeteneklidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="df67a-165">Kod güvenlik için denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="df67a-166">Desenleri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="df67a-166">Override Patterns</span></span>

<span data-ttu-id="df67a-167">Aşağıdaki tablo, düzey 2 saydamlığı için izin verilen yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="df67a-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="df67a-168">Temel sanal/arayüz üyesi</span><span class="sxs-lookup"><span data-stu-id="df67a-168">Base virtual/interface member</span></span>|<span data-ttu-id="df67a-169">Geçersiz kılma/arabirim</span><span class="sxs-lookup"><span data-stu-id="df67a-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="df67a-170">Devralma Kuralları</span><span class="sxs-lookup"><span data-stu-id="df67a-170">Inheritance Rules</span></span>

<span data-ttu-id="df67a-171">Bu bölümde, erişim ve yeteneklere `Critical`göre `SafeCritical` aşağıdaki sıra , ve koda `Transparent`atanır:</span><span class="sxs-lookup"><span data-stu-id="df67a-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="df67a-172">Türleri için kurallar: Soldan sağa gitmek, erişim daha kısıtlayıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="df67a-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="df67a-173">Türetilen türler en az temel tür kadar kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="df67a-174">Yöntem kuralları: Türemiş yöntemler temel yöntemden erişilebilirliği değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="df67a-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="df67a-175">Varsayılan davranış için açıklamalı olmayan tüm türemiş yöntemler. `Transparent`</span><span class="sxs-lookup"><span data-stu-id="df67a-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="df67a-176">Geçersiz türlerin türevleri, geçersiz kılınan yöntem açıkça 'olarak `SecurityCritical`açıklanmazsa, bir özel durum atılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="df67a-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="df67a-177">Aşağıdaki tablo, izin verilen tür devralma desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="df67a-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="df67a-178">Taban sınıf</span><span class="sxs-lookup"><span data-stu-id="df67a-178">Base class</span></span>|<span data-ttu-id="df67a-179">Türemiş sınıf olabilir</span><span class="sxs-lookup"><span data-stu-id="df67a-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="df67a-180">Aşağıdaki tabloda izin verilmeyen tür devralma desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df67a-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="df67a-181">Taban sınıf</span><span class="sxs-lookup"><span data-stu-id="df67a-181">Base class</span></span>|<span data-ttu-id="df67a-182">Türetilmiş sınıf olamaz</span><span class="sxs-lookup"><span data-stu-id="df67a-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="df67a-183">Aşağıdaki tabloda izin verilen yöntem kalıtım desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df67a-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="df67a-184">Temel yöntem</span><span class="sxs-lookup"><span data-stu-id="df67a-184">Base method</span></span>|<span data-ttu-id="df67a-185">Türemiş yöntem,</span><span class="sxs-lookup"><span data-stu-id="df67a-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="df67a-186">Aşağıdaki tabloda izin verilmeyen yöntem kalıtım desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df67a-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="df67a-187">Temel yöntem</span><span class="sxs-lookup"><span data-stu-id="df67a-187">Base method</span></span>|<span data-ttu-id="df67a-188">Türemiş yöntem,</span><span class="sxs-lookup"><span data-stu-id="df67a-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="df67a-189">Bu devralma kuralları düzey 2 türleri ve üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df67a-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="df67a-190">Düzey 1 derlemeleri türleri düzey 2 güvenlik açısından kritik türleri ve üyeleri devralabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="df67a-191">Bu nedenle, düzey 2 türleri ve üyeleri seviye 1 mirasçılar için ayrı miras talepleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="df67a-192">Ek Bilgiler ve Kurallar</span><span class="sxs-lookup"><span data-stu-id="df67a-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="df67a-193">LinkDemand Desteği</span><span class="sxs-lookup"><span data-stu-id="df67a-193">LinkDemand Support</span></span>

<span data-ttu-id="df67a-194">Düzey 2 saydamlık modeli <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> öznitelik ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="df67a-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="df67a-195">Eski (düzey 1) kodunda, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik <xref:System.Security.Permissions.SecurityAction.Demand>olarak bir .</span><span class="sxs-lookup"><span data-stu-id="df67a-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="df67a-196">Yansıma</span><span class="sxs-lookup"><span data-stu-id="df67a-196">Reflection</span></span>

<span data-ttu-id="df67a-197">Kritik bir yöntem çağırmak veya kritik bir alanı okumak tam güven talebini tetikler (tıpkı özel bir yöntem veya alanı çağrıştırıyormuşgibi).</span><span class="sxs-lookup"><span data-stu-id="df67a-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="df67a-198">Bu nedenle, tam güven kodu kritik bir yöntem çağırabilir, kısmi güven kodu ise.</span><span class="sxs-lookup"><span data-stu-id="df67a-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="df67a-199"><xref:System.Reflection> Türü, `SecurityCritical`yöntemi veya alanı , `SecuritySafeCritical`, , , `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, , ve <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="df67a-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="df67a-200">Öznitelik varlığını denetlemek yerine yansımayı kullanarak saydamlığı belirlemek için bu özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="df67a-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="df67a-201">Saydamlık kuralları karmaşıktır ve öznitelik için denetleme yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="df67a-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="df67a-202">Bir `SafeCritical` yöntem `true` hem <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>de `SafeCritical` , çünkü gerçekten kritik (kritik kod olarak aynı özelliklere sahiptir, ancak saydam kod dan çağrılabilir) için döndürür.</span><span class="sxs-lookup"><span data-stu-id="df67a-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="df67a-203">Dinamik yöntemler, bağlı oldukları modüllerin saydamlıklarını devralır; türün saydamlığı (bir türe bağlıysalar) devralınmaz.</span><span class="sxs-lookup"><span data-stu-id="df67a-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="df67a-204">Tam Güven İçinde Doğrulamayı Atlama</span><span class="sxs-lookup"><span data-stu-id="df67a-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="df67a-205">Özelliği öznitelikte ayarlayarak tam güvenilen <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> saydam `true` derlemeler için doğrulamayı <xref:System.Security.SecurityRulesAttribute> atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df67a-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="df67a-206">Özellik <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> varsayılan `false` olarak dır, bu nedenle `true` özelliğin doğrulamayı atlamak için ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="df67a-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="df67a-207">Bu sadece optimizasyon amaçlı yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df67a-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="df67a-208">`transparent` [PEVerify aracındaki](../tools/peverify-exe-peverify-tool.md)seçeneği kullanarak derlemedeki saydam kodun doğrulanabilir olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="df67a-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df67a-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df67a-209">See also</span></span>

- [<span data-ttu-id="df67a-210">Güvenlik-Saydam Kod, Düzey 1</span><span class="sxs-lookup"><span data-stu-id="df67a-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="df67a-211">Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="df67a-211">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
