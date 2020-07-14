---
title: Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş
description: Bir Özeti okuyun ve .NET 4 ' te kod erişimi güvenlik ilkesi uyumluluğu ve geçişi hakkındaki bağlantılara bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: e5affd9d16635fa28342b5b7390a083185975f2b
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281738"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="dc11a-103">Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş</span><span class="sxs-lookup"><span data-stu-id="dc11a-103">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="dc11a-104">Kod erişim güvenliği (CAS) ilke bölümü .NET Framework 4 ' te kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dc11a-104">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="dc11a-105">Sonuç olarak, eski ilke türlerini ve üyelerini [açıkça](#explicit_use) veya [örtük](#implicit_use) olarak çağırırsanız (diğer türler ve Üyeler aracılığıyla) derleme uyarıları ve çalışma zamanı özel durumları ile karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc11a-105">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="dc11a-106">Uyarıları ve hataları aşağıdakilerden birini yaparak önleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc11a-106">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="dc11a-107">Kullanılmayan çağrılar için .NET Framework 4 yerine [geçme](#migration) .</span><span class="sxs-lookup"><span data-stu-id="dc11a-107">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="dc11a-108">\-veya</span><span class="sxs-lookup"><span data-stu-id="dc11a-108">\- or -</span></span>

- <span data-ttu-id="dc11a-109">Eski CAS ilkesi davranışını kabul etmek için [ \<NetFx40_LegacySecurityPolicy> yapılandırma öğesini](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) kullanma.</span><span class="sxs-lookup"><span data-stu-id="dc11a-109">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="dc11a-110">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="dc11a-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="dc11a-111">Açık kullanım</span><span class="sxs-lookup"><span data-stu-id="dc11a-111">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="dc11a-112">Örtülü kullanım</span><span class="sxs-lookup"><span data-stu-id="dc11a-112">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="dc11a-113">Hatalar ve Uyarılar</span><span class="sxs-lookup"><span data-stu-id="dc11a-113">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="dc11a-114">Geçiş: eski çağrılar için değiştirme</span><span class="sxs-lookup"><span data-stu-id="dc11a-114">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="dc11a-115">Uyumluluk: CAS Ilkesi eski seçeneğini kullanma</span><span class="sxs-lookup"><span data-stu-id="dc11a-115">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="dc11a-116">Açık kullanım</span><span class="sxs-lookup"><span data-stu-id="dc11a-116">Explicit Use</span></span>

<span data-ttu-id="dc11a-117">Güvenlik ilkesini doğrudan işleyen veya korumalı alan için CAS ilkesi gerektiren Üyeler artık kullanılmıyor ve varsayılan olarak hata üretecektir.</span><span class="sxs-lookup"><span data-stu-id="dc11a-117">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="dc11a-118">Bunlara şunlar örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dc11a-118">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="dc11a-119">Örtülü kullanım</span><span class="sxs-lookup"><span data-stu-id="dc11a-119">Implicit Use</span></span>

<span data-ttu-id="dc11a-120">Çeşitli derleme yükleme aşırı yüklemeleri, CAS ilkesinin örtük kullanımları nedeniyle hata üretir.</span><span class="sxs-lookup"><span data-stu-id="dc11a-120">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="dc11a-121">Bu aşırı yüklemeler <xref:System.Security.Policy.Evidence> , CAS ilkesini çözümlemek için kullanılan bir parametre alır ve bir derleme için izin verme kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc11a-121">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="dc11a-122">Aşağıda bazı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc11a-122">Here are some examples.</span></span> <span data-ttu-id="dc11a-123">Kullanılmayan aşırı yüklemeler parametre olarak ele alınır <xref:System.Security.Policy.Evidence> :</span><span class="sxs-lookup"><span data-stu-id="dc11a-123">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="dc11a-124">Hatalar ve Uyarılar</span><span class="sxs-lookup"><span data-stu-id="dc11a-124">Errors and Warnings</span></span>

<span data-ttu-id="dc11a-125">Kullanılmayan türler ve Üyeler, kullanıldıkları zaman aşağıdaki hata iletilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc11a-125">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="dc11a-126"><xref:System.Security.Policy.Evidence?displayProperty=nameWithType>Türün kendisinin eski olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dc11a-126">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="dc11a-127">Derleme zamanı uyarısı:</span><span class="sxs-lookup"><span data-stu-id="dc11a-127">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="dc11a-128">Çalışma zamanı özel durumu:</span><span class="sxs-lookup"><span data-stu-id="dc11a-128">Run-time exception:</span></span>

<span data-ttu-id="dc11a-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="dc11a-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="dc11a-130">Geçiş: eski çağrılar için değiştirme</span><span class="sxs-lookup"><span data-stu-id="dc11a-130">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="dc11a-131">Derlemenin güven düzeyini belirleme</span><span class="sxs-lookup"><span data-stu-id="dc11a-131">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="dc11a-132">CAS ilkesi, genellikle bir derlemenin veya uygulama etki alanının izin verme kümesini veya güven düzeyini belirlemede kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc11a-132">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="dc11a-133">.NET Framework 4, güvenlik ilkesini çözümlemek zorunda olmayan aşağıdaki yararlı özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="dc11a-133">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="dc11a-134">Uygulama etki alanı korumalı alana alma</span><span class="sxs-lookup"><span data-stu-id="dc11a-134">Application Domain Sandboxing</span></span>

<span data-ttu-id="dc11a-135"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>Yöntemi genellikle bir uygulama etki alanındaki derlemeler için korumalı alana alma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc11a-135">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="dc11a-136">.NET Framework 4, bu amaçla kullanılması gereken üyeleri kullanıma sunar <xref:System.Security.Policy.PolicyLevel> .</span><span class="sxs-lookup"><span data-stu-id="dc11a-136">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="dc11a-137">Daha fazla bilgi için bkz. [nasıl yapılır: bir korumalı alana kısmen güvenilen kod çalıştırma](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="dc11a-137">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="dc11a-138">Kısmen güvenilen kod için güvenli veya makul bir Izin kümesi belirleme</span><span class="sxs-lookup"><span data-stu-id="dc11a-138">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="dc11a-139">Ana bilgisayarların, genellikle korumalı alana alma barındırılan kodu için uygun izinleri belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc11a-139">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="dc11a-140">.NET Framework 4 ' den önce, CAS ilkesi yöntemi ile bunu yapmak için bir yol sağladı <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc11a-140">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dc11a-141">Bunun yerine, .NET Framework 4, <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> sağlanan kanıt için güvenli, standart bir izin kümesi döndüren yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc11a-141">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="dc11a-142">Korumalı alana alma olmayan senaryolar: derleme yükleri için aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="dc11a-142">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="dc11a-143">Derleme yükü aşırı yüklemesi kullanmanın nedeni, derleme korumalı alana alma yerine, aksi durumda kullanılamayan parametreleri kullanmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc11a-143">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="dc11a-144">.NET Framework 4 ' den başlayarak, bir parametre olarak bir nesne gerektirmeyen derleme yükü aşırı yüklemeleri, <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> Örneğin, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType> Bu senaryoyu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="dc11a-144">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="dc11a-145">Bir derlemenin korumalı alanını istiyorsanız, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yüklemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="dc11a-145">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="dc11a-146">Uyumluluk: CAS Ilkesi eski seçeneğini kullanma</span><span class="sxs-lookup"><span data-stu-id="dc11a-146">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="dc11a-147">[ \<NetFx40_LegacySecurityPolicy> Yapılandırma öğesi](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) bir işlemin veya kitaplığın eski CAS ilkesini kullanmasını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dc11a-147">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="dc11a-148">Bu öğeyi etkinleştirdiğinizde, ilke ve kanıt aşırı yüklemeleri Framework 'ün önceki sürümlerinde olduğu gibi çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="dc11a-148">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="dc11a-149">CAS ilkesi davranışı çalışma zamanı sürümü temelinde belirtilmiştir, bu nedenle bir çalışma zamanı sürümü için CAS ilkesini değiştirmek, başka bir sürümün CAS ilkesini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="dc11a-149">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="dc11a-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc11a-150">See also</span></span>

- [<span data-ttu-id="dc11a-151">Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dc11a-151">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="dc11a-152">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dc11a-152">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
