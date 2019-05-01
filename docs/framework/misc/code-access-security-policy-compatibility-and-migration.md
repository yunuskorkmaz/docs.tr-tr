---
title: Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d9281e52de43391a92262f85084715ccabd5515
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868920"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="f0d9c-102">Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş</span><span class="sxs-lookup"><span data-stu-id="f0d9c-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="f0d9c-103">Kod erişimi güvenliği (CAS) ilkesi kısmı eski yapılmış [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0d9c-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="f0d9c-104">Geçersiz ilke türleri ve üyeleri çağırırsanız sonuç olarak, derleme uyarıları ve çalışma zamanı özel durumları karşılaşabileceğiniz [açıkça](#explicit_use) veya [örtük olarak](#implicit_use) (aracılığıyla, diğer türler ve Üyeler).</span><span class="sxs-lookup"><span data-stu-id="f0d9c-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="f0d9c-105">Ya da uyarıları ve hataları önleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="f0d9c-106">[Geçiş](#migration) için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] eski çağrıları için değişiklik.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>

   <span data-ttu-id="f0d9c-107">\- veya -</span><span class="sxs-lookup"><span data-stu-id="f0d9c-107">\- or -</span></span>

- <span data-ttu-id="f0d9c-108">Kullanarak [< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) eski CAS ilkesi davranışı kabul etme.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="f0d9c-109">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="f0d9c-110">Açık kullanın</span><span class="sxs-lookup"><span data-stu-id="f0d9c-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="f0d9c-111">Örtük kullanım</span><span class="sxs-lookup"><span data-stu-id="f0d9c-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="f0d9c-112">Hatalar ve Uyarılar</span><span class="sxs-lookup"><span data-stu-id="f0d9c-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="f0d9c-113">Geçişi: Eski çağrıları için değiştirme</span><span class="sxs-lookup"><span data-stu-id="f0d9c-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="f0d9c-114">Uyumluluk: Eski CAS ilkesini seçeneğiyle</span><span class="sxs-lookup"><span data-stu-id="f0d9c-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="f0d9c-115">Açık kullanın</span><span class="sxs-lookup"><span data-stu-id="f0d9c-115">Explicit Use</span></span>

<span data-ttu-id="f0d9c-116">Korumalı alan için CAS ilkesini doğrudan güvenlik ilkesini değiştirmek veya üyeleri artık kullanılmayan ve varsayılan olarak hataya neden.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="f0d9c-117">Bu örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="f0d9c-118">Örtük kullanım</span><span class="sxs-lookup"><span data-stu-id="f0d9c-118">Implicit Use</span></span>

<span data-ttu-id="f0d9c-119">Birkaç derleme yükleme üretim hataları örtük kendi CAS ilkesini kullanımı nedeniyle aşırı.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="f0d9c-120">Bu aşırı yüklemeler ele bir <xref:System.Security.Policy.Evidence> CAS ilkesini çözmek ve izin sağlamak için kullanılan parametre kümesi için bir derleme verin.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="f0d9c-121">Bazı örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-121">Here are some examples.</span></span> <span data-ttu-id="f0d9c-122">Alan geçersiz aşırı olanlardır <xref:System.Security.Policy.Evidence> bir parametre olarak:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="f0d9c-123">Hatalar ve Uyarılar</span><span class="sxs-lookup"><span data-stu-id="f0d9c-123">Errors and Warnings</span></span>

<span data-ttu-id="f0d9c-124">Kullanıldıklarında aşağıdaki hata iletilerinden artık kullanılmayan türler ve üyeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="f0d9c-125">Unutmayın <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> türün kendisine eski değil.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="f0d9c-126">Derleme zamanı uyarısı:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="f0d9c-127">Çalışma zamanı özel durum:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-127">Run-time exception:</span></span>

<span data-ttu-id="f0d9c-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="f0d9c-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="f0d9c-129">Geçişi: Eski çağrıları için değiştirme</span><span class="sxs-lookup"><span data-stu-id="f0d9c-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="f0d9c-130">Bir derlemenin güven düzeyine belirleme</span><span class="sxs-lookup"><span data-stu-id="f0d9c-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="f0d9c-131">CAS ilkesini genellikle bir derlemenin belirlemek için kullanılan veya uygulama etki alanının izin kümesi vermek ya da güven düzeyi.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="f0d9c-132">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Güvenlik ilkesi çözmek zorunda değildir yararlı aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="f0d9c-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="f0d9c-133">Uygulama etki alanı korumalı alana alma</span><span class="sxs-lookup"><span data-stu-id="f0d9c-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="f0d9c-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Yöntemi, genellikle uygulama etki alanında derlemeleri korumalı alana alma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="f0d9c-135">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Kullanmak zorunda değilsiniz üyeleri ortaya koyar <xref:System.Security.Policy.PolicyLevel> bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="f0d9c-136">Daha fazla bilgi için [nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="f0d9c-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="f0d9c-137">Kısmen güvenli ya da makul bir izin için kümesinin belirleme güvenilen kod</span><span class="sxs-lookup"><span data-stu-id="f0d9c-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="f0d9c-138">Ana bilgisayar genellikle barındırılan bir korumalı alana alma kodu için uygun izinler belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="f0d9c-139">Önce [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS ilkesini sağlanan ile bunu yapmanın bir yolu <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f0d9c-140">Bir değişiklik olarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sağlar <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> yöntemi için sağlanan kanıt kümesi güvenli, standart bir izin verir.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="f0d9c-141">Korumalı alana alma olmayan senaryolar: Derleme yüklerini için aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="f0d9c-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="f0d9c-142">Aksi takdirde derleme korumalı alana alma yerine mevcut olmayan parametreleri kullanmak bir derleme yük aşırı kullanılmasının nedeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="f0d9c-143">İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], gerekli olmayan derleme yük aşırı yüklemeler bir <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> bir bu gibi bir durumda parametre olarak nesne <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, bu senaryoyu etkinleştirmek.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="f0d9c-144">Korumalı alan için bir derleme istiyorsanız kullanın <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="f0d9c-145">Uyumluluk: Eski CAS ilkesini seçeneğiyle</span><span class="sxs-lookup"><span data-stu-id="f0d9c-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="f0d9c-146">[< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) bir işlem veya kitaplık eski CAS ilkesini kullanan belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="f0d9c-147">Bu öğe etkinleştirdiğinizde, ilke ve kanıt aşırı framework'ün önceki sürümlerinde olduğu gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="f0d9c-148">Bir çalışma zamanı sürümü için CAS ilkesini değiştirme başka bir sürümü CAS ilkesini etkilemez bu nedenle CA ilkesi davranışını bir çalışma zamanı sürümü temelinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f0d9c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0d9c-149">See also</span></span>

- [<span data-ttu-id="f0d9c-150">Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f0d9c-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="f0d9c-151">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f0d9c-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
