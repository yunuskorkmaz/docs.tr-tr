---
title: Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9563dae9ba5d144300549e7f33f5f5a9feb1d410
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205640"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="d9b06-102">Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş</span><span class="sxs-lookup"><span data-stu-id="d9b06-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="d9b06-103">Kod erişim güvenliği (CAS) ilke bölümü .NET Framework 4 ' te kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d9b06-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="d9b06-104">Sonuç olarak, eski ilke türlerini ve üyelerini [açıkça](#explicit_use) veya [örtük](#implicit_use) olarak çağırırsanız (diğer türler ve Üyeler aracılığıyla) derleme uyarıları ve çalışma zamanı özel durumları ile karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9b06-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="d9b06-105">Uyarıları ve hataları aşağıdakilerden birini yaparak önleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d9b06-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="d9b06-106">Kullanılmayan çağrılar için .NET Framework 4 yerine [geçme](#migration) .</span><span class="sxs-lookup"><span data-stu-id="d9b06-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="d9b06-107">\- veya -</span><span class="sxs-lookup"><span data-stu-id="d9b06-107">\- or -</span></span>

- <span data-ttu-id="d9b06-108">Eski CAS ilkesi davranışını kabul etmek için [ NetFx40_LegacySecurityPolicy>yapılandırmaöğesinikullanma.\<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9b06-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="d9b06-109">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="d9b06-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="d9b06-110">Açık kullanım</span><span class="sxs-lookup"><span data-stu-id="d9b06-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="d9b06-111">Örtülü kullanım</span><span class="sxs-lookup"><span data-stu-id="d9b06-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="d9b06-112">Hatalar ve Uyarılar</span><span class="sxs-lookup"><span data-stu-id="d9b06-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="d9b06-113">Geçiş Eski çağrılar için değiştirme</span><span class="sxs-lookup"><span data-stu-id="d9b06-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="d9b06-114">Kları CAS Ilkesi eski seçeneğini kullanma</span><span class="sxs-lookup"><span data-stu-id="d9b06-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="d9b06-115">Açık kullanım</span><span class="sxs-lookup"><span data-stu-id="d9b06-115">Explicit Use</span></span>

<span data-ttu-id="d9b06-116">Güvenlik ilkesini doğrudan işleyen veya korumalı alan için CAS ilkesi gerektiren Üyeler artık kullanılmıyor ve varsayılan olarak hata üretecektir.</span><span class="sxs-lookup"><span data-stu-id="d9b06-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="d9b06-117">Bunlara şunlar örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d9b06-117">Examples of these are:</span></span>

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a><span data-ttu-id="d9b06-118">Örtülü kullanım</span><span class="sxs-lookup"><span data-stu-id="d9b06-118">Implicit Use</span></span>

<span data-ttu-id="d9b06-119">Çeşitli derleme yükleme aşırı yüklemeleri, CAS ilkesinin örtük kullanımları nedeniyle hata üretir.</span><span class="sxs-lookup"><span data-stu-id="d9b06-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="d9b06-120">Bu aşırı yüklemeler, <xref:System.Security.Policy.Evidence> CAS ilkesini çözümlemek için kullanılan bir parametre alır ve bir derleme için izin verme kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9b06-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="d9b06-121">Bazı örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9b06-121">Here are some examples.</span></span> <span data-ttu-id="d9b06-122">Kullanılmayan aşırı yüklemeler parametre olarak ele <xref:System.Security.Policy.Evidence> alınır:</span><span class="sxs-lookup"><span data-stu-id="d9b06-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a><span data-ttu-id="d9b06-123">Hatalar ve Uyarılar</span><span class="sxs-lookup"><span data-stu-id="d9b06-123">Errors and Warnings</span></span>

<span data-ttu-id="d9b06-124">Kullanılmayan türler ve Üyeler, kullanıldıkları zaman aşağıdaki hata iletilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9b06-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="d9b06-125"><xref:System.Security.Policy.Evidence?displayProperty=nameWithType> Türün kendisinin eski olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d9b06-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="d9b06-126">Derleme zamanı uyarısı:</span><span class="sxs-lookup"><span data-stu-id="d9b06-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="d9b06-127">Çalışma zamanı özel durumu:</span><span class="sxs-lookup"><span data-stu-id="d9b06-127">Run-time exception:</span></span>

<span data-ttu-id="d9b06-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="d9b06-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="d9b06-129">Geçiş Eski çağrılar için değiştirme</span><span class="sxs-lookup"><span data-stu-id="d9b06-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="d9b06-130">Derlemenin güven düzeyini belirleme</span><span class="sxs-lookup"><span data-stu-id="d9b06-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="d9b06-131">CAS ilkesi, genellikle bir derlemenin veya uygulama etki alanının izin verme kümesini veya güven düzeyini belirlemede kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9b06-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="d9b06-132">.NET Framework 4, güvenlik ilkesini çözümlemek zorunda olmayan aşağıdaki yararlı özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="d9b06-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="d9b06-133">Uygulama etki alanı korumalı alana alma</span><span class="sxs-lookup"><span data-stu-id="d9b06-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="d9b06-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Yöntemi genellikle bir uygulama etki alanındaki derlemeler için korumalı alana alma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9b06-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="d9b06-135">.NET Framework 4, bu amaçla kullanılması <xref:System.Security.Policy.PolicyLevel> gereken üyeleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d9b06-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="d9b06-136">Daha fazla bilgi için [nasıl yapılır: Bir korumalı alanda](how-to-run-partially-trusted-code-in-a-sandbox.md)kısmen güvenilen kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d9b06-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="d9b06-137">Kısmen güvenilen kod için güvenli veya makul bir Izin kümesi belirleme</span><span class="sxs-lookup"><span data-stu-id="d9b06-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="d9b06-138">Ana bilgisayarların, genellikle korumalı alana alma barındırılan kodu için uygun izinleri belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9b06-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="d9b06-139">.NET Framework 4 ' den önce, CAS ilkesi <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> yöntemi ile bunu yapmak için bir yol sağladı.</span><span class="sxs-lookup"><span data-stu-id="d9b06-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d9b06-140">Bunun yerine, .NET Framework 4, sağlanan kanıt <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> için güvenli, standart bir izin kümesi döndüren yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9b06-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="d9b06-141">Korumalı alana alma olmayan senaryolar: Derleme yükleri için aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="d9b06-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="d9b06-142">Derleme yükü aşırı yüklemesi kullanmanın nedeni, derleme korumalı alana alma yerine, aksi durumda kullanılamayan parametreleri kullanmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9b06-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="d9b06-143">.NET Framework 4 ' den başlayarak, bir parametre olarak bir <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> nesne gerektirmeyen derleme yükü aşırı yüklemeleri, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>Örneğin, bu senaryoyu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d9b06-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="d9b06-144">Bir derlemenin korumalı alanını istiyorsanız, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yüklemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9b06-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="d9b06-145">Kları CAS Ilkesi eski seçeneğini kullanma</span><span class="sxs-lookup"><span data-stu-id="d9b06-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="d9b06-146">NetFx40_LegacySecurityPolicy > Configuration öğesi bir işlemin veya kitaplığın eski CAS ilkesini kullanmasını belirtmenize olanak tanır. [ \<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9b06-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="d9b06-147">Bu öğeyi etkinleştirdiğinizde, ilke ve kanıt aşırı yüklemeleri Framework 'ün önceki sürümlerinde olduğu gibi çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="d9b06-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="d9b06-148">CAS ilkesi davranışı çalışma zamanı sürümü temelinde belirtilmiştir, bu nedenle bir çalışma zamanı sürümü için CAS ilkesini değiştirmek, başka bir sürümün CAS ilkesini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d9b06-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d9b06-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b06-149">See also</span></span>

- [<span data-ttu-id="d9b06-150">Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır</span><span class="sxs-lookup"><span data-stu-id="d9b06-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="d9b06-151">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d9b06-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
