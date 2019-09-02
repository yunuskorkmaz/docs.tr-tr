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
ms.openlocfilehash: 61a436efe3e3af7ce4aa50afe242838b1cd8941e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206074"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="0c284-102">Güvenliği Saydam Kod, 2. Düzey</span><span class="sxs-lookup"><span data-stu-id="0c284-102">Security-Transparent Code, Level 2</span></span>

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="0c284-103">Düzey 2 saydamlık .NET Framework 4 ' te tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="0c284-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="0c284-104">Bu modelin üç listesi saydam kod, güvenli güvenlik açısından kritik kod ve güvenlik açısından kritik koddur.</span><span class="sxs-lookup"><span data-stu-id="0c284-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="0c284-105">Tam güven olarak çalışan kod dahil saydam kod, yalnızca diğer saydam kodu veya güvenlik açısından güvenli kritik kodu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="0c284-106">Yalnızca etki alanının kısmi güven izin kümesi (varsa) tarafından izin verilen eylemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="0c284-107">Saydam kod şunları yapılamıyor:</span><span class="sxs-lookup"><span data-stu-id="0c284-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="0c284-108">Bir <xref:System.Security.CodeAccessPermission.Assert%2A> ayrıcalık yükselmesi veya yükseltmesi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0c284-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="0c284-109">Güvenli olmayan veya doğrulanamayan kod içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0c284-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="0c284-110">Kritik kodu doğrudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="0c284-110">Directly call critical code.</span></span>

  - <span data-ttu-id="0c284-111">Yerel kodu veya kodu <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğiyle çağırın.</span><span class="sxs-lookup"><span data-stu-id="0c284-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="0c284-112">Tarafından korunan bir üyeyi çağırın <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="0c284-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="0c284-113">Kritik türlerden devralma.</span><span class="sxs-lookup"><span data-stu-id="0c284-113">Inherit from critical types.</span></span>

  <span data-ttu-id="0c284-114">Ayrıca, saydam Yöntemler kritik sanal yöntemleri geçersiz kılamaz veya kritik arabirim yöntemleri uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="0c284-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="0c284-115">Güvenli kritik kod tamamen güvenilirdir, ancak saydam kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="0c284-116">Tam güven kodunun sınırlı bir yüzey alanını kullanıma sunar; güvenli kritik kodda doğruluk ve güvenlik doğrulamaları meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="0c284-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="0c284-117">Güvenlik açısından kritik kod herhangi bir kodu çağırabilir ve tamamen güvenilirdir, ancak saydam kod tarafından çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c284-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

<span data-ttu-id="0c284-118">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="0c284-118">This topic contains the following sections:</span></span>

- [<span data-ttu-id="0c284-119">Kullanım örnekleri ve davranışlar</span><span class="sxs-lookup"><span data-stu-id="0c284-119">Usage Examples and Behaviors</span></span>](#examples)

- [<span data-ttu-id="0c284-120">Geçersiz kılma desenleri</span><span class="sxs-lookup"><span data-stu-id="0c284-120">Override Patterns</span></span>](#override)

- [<span data-ttu-id="0c284-121">Devralma kuralları</span><span class="sxs-lookup"><span data-stu-id="0c284-121">Inheritance Rules</span></span>](#inheritance)

- [<span data-ttu-id="0c284-122">Ek bilgi ve kurallar</span><span class="sxs-lookup"><span data-stu-id="0c284-122">Additional Information and Rules</span></span>](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="0c284-123">Kullanım Örnekleri ve Davranışlar</span><span class="sxs-lookup"><span data-stu-id="0c284-123">Usage Examples and Behaviors</span></span>

<span data-ttu-id="0c284-124">.NET Framework 4 kuralları belirtmek için (düzey 2 saydamlık), bir derleme için aşağıdaki ek açıklamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="0c284-124">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="0c284-125">.NET Framework 2,0 kurallarına (düzey 1 saydamlık) kilitlemek için aşağıdaki ek açıklamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="0c284-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="0c284-126">Bir derlemeye Not eklemek istemiyorsanız, varsayılan olarak .NET Framework 4 kuralları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c284-126">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="0c284-127">Ancak önerilen en iyi yöntem, varsayılan değere göre değil <xref:System.Security.SecurityRulesAttribute> , özniteliğini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0c284-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="0c284-128">Bütünleştirilmiş kod genelinde ek açıklama</span><span class="sxs-lookup"><span data-stu-id="0c284-128">Assembly-wide Annotation</span></span>

<span data-ttu-id="0c284-129">Aşağıdaki kurallar, derleme düzeyinde özniteliklerin kullanımı için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0c284-129">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="0c284-130">Öznitelik yok: Herhangi bir öznitelik belirtmezseniz, çalışma zamanı tüm kodu güvenlik açısından kritik olarak yorumlar ve güvenlik açısından kritik olduğu durumlar dışında, bir devralma kuralını ihlal ediyor (örneğin, bir saydam sanal veya arabirim yöntemi geçersiz kılırken veya uygularken).</span><span class="sxs-lookup"><span data-stu-id="0c284-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="0c284-131">Bu durumlarda, Yöntemler güvenli öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0c284-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="0c284-132">Hiçbir öznitelik belirtilmesi, ortak dil çalışma zamanının sizin için saydamlık kurallarını belirlemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c284-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="0c284-133">`SecurityTransparent`: Tüm kod saydamdır; Tüm derleme ayrıcalıklı veya güvenli olmayan hiçbir işlem yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0c284-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="0c284-134">`SecurityCritical`: Bu derlemedeki türler tarafından tanıtılan tüm kodlar kritiktir; diğer tüm kodlar saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="0c284-135">Bu senaryo herhangi bir öznitelik Belirtmemeye benzer; Ancak, ortak dil çalışma zamanı, saydamlık kurallarını otomatik olarak belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="0c284-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="0c284-136">Örneğin, bir sanal veya soyut yöntemi geçersiz kılarsınız veya bir arabirim yöntemi uygularsanız, varsayılan olarak bu yöntem saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="0c284-137">Yöntemine `SecurityCritical` açıkçaAçıklama<xref:System.TypeLoadException> eklemek zorundasınız ;Aksitakdirde,yüklemezamanındabiroluşturulur.`SecuritySafeCritical`</span><span class="sxs-lookup"><span data-stu-id="0c284-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="0c284-138">Bu kural, hem temel sınıf hem de türetilmiş sınıf aynı derlemede olduğunda da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0c284-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="0c284-139">`AllowPartiallyTrustedCallers`(yalnızca düzey 2): Tüm kod varsayılan olarak saydam olur.</span><span class="sxs-lookup"><span data-stu-id="0c284-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="0c284-140">Ancak, ayrı türler ve üyelerin diğer öznitelikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-140">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="0c284-141">Aşağıdaki tabloda düzey 1 düzeyi 2 için derleme düzeyi davranışı karşılaştırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c284-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="0c284-142">Derleme özniteliği</span><span class="sxs-lookup"><span data-stu-id="0c284-142">Assembly attribute</span></span>|<span data-ttu-id="0c284-143">Düzey 2</span><span class="sxs-lookup"><span data-stu-id="0c284-143">Level 2</span></span>|<span data-ttu-id="0c284-144">Düzey 1</span><span class="sxs-lookup"><span data-stu-id="0c284-144">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="0c284-145">Kısmen güvenilen bir derlemede öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="0c284-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="0c284-146">Türler ve Üyeler varsayılan olarak saydamdır, ancak güvenlik açısından kritik veya güvenlik açısından kritik öneme sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="0c284-147">Tüm türler ve Üyeler saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-147">All types and members are transparent.</span></span>|
|<span data-ttu-id="0c284-148">Öznitelik yok</span><span class="sxs-lookup"><span data-stu-id="0c284-148">No attribute</span></span>|<span data-ttu-id="0c284-149">Hiçbir öznitelik belirtilmesi, ortak dil çalışma zamanının sizin için saydamlık kurallarını belirlemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c284-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="0c284-150">Güvenlik açısından kritik olduğu durumlar dışında, bir devralma kuralını ihlal ettiğinden, tüm türler ve Üyeler güvenlik açısından kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0c284-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="0c284-151">Tam güvenilir bir derlemede (genel derleme önbelleğinde veya ' de `AppDomain`tam güven olarak tanımlanır) tüm türler saydamdır ve tüm Üyeler güvenlik açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="0c284-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="0c284-152">Tüm türler ve Üyeler saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-152">All types and members are transparent.</span></span>|<span data-ttu-id="0c284-153">Tüm türler ve Üyeler saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-153">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="0c284-154">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="0c284-154">Not applicable.</span></span>|<span data-ttu-id="0c284-155">Tüm türler ve Üyeler güvenlik açısından kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0c284-155">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="0c284-156">Bu derlemedeki türler tarafından tanıtılan tüm kodlar kritiktir; diğer tüm kodlar saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="0c284-157">Bir sanal veya soyut yöntemi geçersiz kılarsınız veya bir arabirim yöntemi uygularsanız, yöntemi veya `SecurityCritical` `SecuritySafeCritical`olarak açıkça not almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c284-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="0c284-158">Tüm kod varsayılan olarak saydam olur.</span><span class="sxs-lookup"><span data-stu-id="0c284-158">All code defaults to transparent.</span></span> <span data-ttu-id="0c284-159">Ancak, ayrı türler ve üyelerin diğer öznitelikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-159">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="0c284-160">Tür ve Üye Ek Açıklaması</span><span class="sxs-lookup"><span data-stu-id="0c284-160">Type and Member Annotation</span></span>

<span data-ttu-id="0c284-161">Bir türe uygulanan güvenlik öznitelikleri, türü tarafından tanıtılan Üyeler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0c284-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="0c284-162">Ancak, temel sınıfın veya arabirim uygulamalarının sanal veya soyut geçersiz kılmaları için uygulanmazlar.</span><span class="sxs-lookup"><span data-stu-id="0c284-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="0c284-163">Aşağıdaki kurallar, tür ve üye düzeyinde özniteliklerin kullanımı için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0c284-163">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="0c284-164">`SecurityCritical`: Tür veya üye kritiktir ve yalnızca tam güven kodu tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="0c284-165">Güvenlik açısından kritik bir tür içinde sunulan yöntemler kritiktir.</span><span class="sxs-lookup"><span data-stu-id="0c284-165">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0c284-166">Temel sınıflarda veya arabirimlerde tanıtılan ve güvenlik açısından kritik bir sınıfta geçersiz kılınan veya uygulanan sanal ve soyut yöntemler varsayılan olarak saydamdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="0c284-167">`SecuritySafeCritical` Ya`SecurityCritical`da olarak tanımlanmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c284-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="0c284-168">`SecuritySafeCritical`: Tür veya üye güvenli kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0c284-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="0c284-169">Ancak, tür veya üye saydam (kısmen güvenilir) koddan çağrılabilir ve diğer kritik kodlar gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="0c284-170">Kod güvenlik için denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0c284-170">The code must be audited for security.</span></span>

[<span data-ttu-id="0c284-171">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0c284-171">Back to top</span></span>](#top)

<a name="override"></a>

## <a name="override-patterns"></a><span data-ttu-id="0c284-172">Desenleri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="0c284-172">Override Patterns</span></span>

<span data-ttu-id="0c284-173">Aşağıdaki tabloda düzey 2 saydamlığına izin verilen yöntem geçersiz kılmaları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c284-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="0c284-174">Taban sanal/arabirim üyesi</span><span class="sxs-lookup"><span data-stu-id="0c284-174">Base virtual/interface member</span></span>|<span data-ttu-id="0c284-175">Geçersiz kılma/arabirim</span><span class="sxs-lookup"><span data-stu-id="0c284-175">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[<span data-ttu-id="0c284-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0c284-176">Back to top</span></span>](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a><span data-ttu-id="0c284-177">Devralma Kuralları</span><span class="sxs-lookup"><span data-stu-id="0c284-177">Inheritance Rules</span></span>

<span data-ttu-id="0c284-178">Bu bölümde, erişim ve yeteneklere göre aşağıdaki sıra `Transparent`, `Critical`ve `SafeCritical` koduna atanır:</span><span class="sxs-lookup"><span data-stu-id="0c284-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="0c284-179">Türlerin kuralları: Soldan sağa doğru gidip erişim daha kısıtlayıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0c284-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="0c284-180">Türetilmiş türler, temel tür olarak en az kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-180">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="0c284-181">Yöntemler için kurallar: Türetilmiş yöntemler, taban yönteminden erişilebilirliği değiştiremezler.</span><span class="sxs-lookup"><span data-stu-id="0c284-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="0c284-182">Varsayılan davranış için, açıklama eklenmiş olmayan tüm türetilmiş yöntemler vardır `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="0c284-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="0c284-183">Kritik türlerin türettiği, geçersiz kılınan yöntemin olarak `SecurityCritical`açıkça açıklanmadığı durumlarda bir özel durumun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c284-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="0c284-184">Aşağıdaki tabloda, izin verilen tür devralma desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c284-184">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="0c284-185">Temel sınıf</span><span class="sxs-lookup"><span data-stu-id="0c284-185">Base class</span></span>|<span data-ttu-id="0c284-186">Türetilmiş sınıf</span><span class="sxs-lookup"><span data-stu-id="0c284-186">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="0c284-187">Aşağıdaki tabloda izin verilmeyen tür devralma desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c284-187">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="0c284-188">Temel sınıf</span><span class="sxs-lookup"><span data-stu-id="0c284-188">Base class</span></span>|<span data-ttu-id="0c284-189">Türetilmiş sınıf olamaz</span><span class="sxs-lookup"><span data-stu-id="0c284-189">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="0c284-190">Aşağıdaki tabloda izin verilen yöntem devralma desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c284-190">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="0c284-191">Base yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c284-191">Base method</span></span>|<span data-ttu-id="0c284-192">Türetilmiş yöntem şu şekilde olabilir</span><span class="sxs-lookup"><span data-stu-id="0c284-192">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="0c284-193">Aşağıdaki tabloda izin verilmeyen Yöntem devralma desenleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c284-193">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="0c284-194">Base yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c284-194">Base method</span></span>|<span data-ttu-id="0c284-195">Türetilmiş yöntem olamaz</span><span class="sxs-lookup"><span data-stu-id="0c284-195">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="0c284-196">Bu devralma kuralları, düzey 2 türleri ve üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0c284-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="0c284-197">Düzey 1 derlemelerdeki türler, düzey 2 güvenlik açısından kritik türlerden ve üyelerden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="0c284-198">Bu nedenle, düzey 2 türleri ve üyeleri, düzey 1 ınheritörler için ayrı devralma taleplerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

[<span data-ttu-id="0c284-199">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0c284-199">Back to top</span></span>](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a><span data-ttu-id="0c284-200">Ek Bilgiler ve Kurallar</span><span class="sxs-lookup"><span data-stu-id="0c284-200">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="0c284-201">LinkDemand Desteği</span><span class="sxs-lookup"><span data-stu-id="0c284-201">LinkDemand Support</span></span>

<span data-ttu-id="0c284-202">Düzey 2 saydamlık modeli, <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> öğesinin özniteliğiyle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="0c284-203">Eski (düzey 1) kodda, bir <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik olarak bir <xref:System.Security.Permissions.SecurityAction.Demand>olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="0c284-204">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0c284-204">Reflection</span></span>

<span data-ttu-id="0c284-205">Kritik bir yöntemi çağırmak veya kritik bir alanı okumak, tam güven için bir talep tetikler (özel bir yöntem veya alan çağırmak gibi).</span><span class="sxs-lookup"><span data-stu-id="0c284-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="0c284-206">Bu nedenle, tam güven kodu kritik bir yöntemi çağırabilir, ancak kısmi güven kodu olamaz.</span><span class="sxs-lookup"><span data-stu-id="0c284-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="0c284-207">Türü <xref:System.Reflection> , yöntemi veya alanı `SecuritySafeCritical` `SecurityCritical` `SecurityTransparent` ,,<xref:System.Type.IsSecurityCritical%2A>veya: ,,<xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>ve olduğunu anlamak için, ad alanına aşağıdaki özellikler eklenmiştir. <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A></span><span class="sxs-lookup"><span data-stu-id="0c284-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="0c284-208">Özniteliğin varlığını denetlemek yerine, yansımayı kullanarak saydamlığı öğrenmek için bu özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c284-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="0c284-209">Saydamlık kuralları karmaşıktır ve öznitelik denetimi yeterli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0c284-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="0c284-210">Bir `SafeCritical` yöntemi <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, `true` , `SafeCritical` gerçekten <xref:System.Type.IsSecurityCritical%2A> kritik olduğundan (kritik kodla aynı yeteneklere sahiptir ancak saydam koddan çağrılabilir), her ikisi için de döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0c284-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="0c284-211">Dinamik yöntemler, eklendiği modüllerin saydamlığını miras alır; Bunlar, türün saydamlığını (bir türe eklenmişse) almayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0c284-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="0c284-212">Tam Güven İçinde Doğrulamayı Atlama</span><span class="sxs-lookup"><span data-stu-id="0c284-212">Skip Verification in Full Trust</span></span>

<span data-ttu-id="0c284-213"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Özelliği<xref:System.Security.SecurityRulesAttribute> özniteliğinde olarak ayarlayarak, tamamen güvenilir saydam derlemeler için doğrulamayı atlayabilirsiniz: `true`</span><span class="sxs-lookup"><span data-stu-id="0c284-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="0c284-214">Özelliği varsayılan olarak `false` olduğundan, doğrulama atlamak için özelliği olarak `true` ayarlanmalıdır. <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A></span><span class="sxs-lookup"><span data-stu-id="0c284-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="0c284-215">Bu yalnızca iyileştirme amacıyla yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c284-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="0c284-216">Derleme içindeki saydam kodun, `transparent` [PEVerify aracında](../tools/peverify-exe-peverify-tool.md)seçeneğini kullanarak doğrulanabilir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c284-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c284-217">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c284-217">See also</span></span>

- [<span data-ttu-id="0c284-218">Güvenliği saydam kod, düzey 1</span><span class="sxs-lookup"><span data-stu-id="0c284-218">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="0c284-219">Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0c284-219">Security Changes</span></span>](../security/security-changes.md)
