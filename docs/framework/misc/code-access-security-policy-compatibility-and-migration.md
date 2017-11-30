---
title: "Kod Erişimi Güvenliği İlkesi Uyumluluğu ve Geçiş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29e81f5e83bc3cbf9467c7940ba6acfd0a8c99b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="44903-102">Kod Erişimi Güvenliği İlkesi Uyumluluğu ve Geçiş</span><span class="sxs-lookup"><span data-stu-id="44903-102">Code Access Security Policy Compatibility and Migration</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="44903-103">Kod erişim güvenliği (CAS) ilkesi kısmı'te eski haline getirilmiştir [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44903-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="44903-104">Geçersiz ilke türleri ve üyeleri çağırırsanız sonuç olarak, derleme uyarıları ve çalışma zamanı özel durumları karşılaşabileceğiniz [açıkça](#explicit_use) veya [örtük olarak](#implicit_use) (aracılığıyla, diğer türleri ve üyeleri).</span><span class="sxs-lookup"><span data-stu-id="44903-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>  
  
 <span data-ttu-id="44903-105">Ya da uyarıları ve hataları önleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44903-105">You can avoid the warnings and errors by either:</span></span>  
  
-   <span data-ttu-id="44903-106">[Geçiş](#migration) için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] eski çağrıları donanımlarının.</span><span class="sxs-lookup"><span data-stu-id="44903-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>  
  
     <span data-ttu-id="44903-107">\-veya -</span><span class="sxs-lookup"><span data-stu-id="44903-107">\- or -</span></span>  
  
-   <span data-ttu-id="44903-108">Kullanarak [< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) eski CA ilke davranışı kabul etmek için.</span><span class="sxs-lookup"><span data-stu-id="44903-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>  
  
 <span data-ttu-id="44903-109">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="44903-109">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="44903-110">Açık kullanın</span><span class="sxs-lookup"><span data-stu-id="44903-110">Explicit Use</span></span>](#explicit_use)  
  
-   [<span data-ttu-id="44903-111">Örtük kullanın</span><span class="sxs-lookup"><span data-stu-id="44903-111">Implicit Use</span></span>](#implicit_use)  
  
-   [<span data-ttu-id="44903-112">Hatalar ve uyarılar</span><span class="sxs-lookup"><span data-stu-id="44903-112">Errors and Warnings</span></span>](#errors_and_warnings)  
  
-   [<span data-ttu-id="44903-113">Geçiş: Artık kullanılmayan çağrıları değiştirme</span><span class="sxs-lookup"><span data-stu-id="44903-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)  
  
-   [<span data-ttu-id="44903-114">Uyumluluğu: CA ilke eski seçeneği kullanma</span><span class="sxs-lookup"><span data-stu-id="44903-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a><span data-ttu-id="44903-115">Açık kullanın</span><span class="sxs-lookup"><span data-stu-id="44903-115">Explicit Use</span></span>  
 <span data-ttu-id="44903-116">Güvenlik ilkesini değiştirmek veya korumalı alan için CA ilke iste doğrudan üyeleri eskidir ve hataları varsayılan olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44903-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>  
  
 <span data-ttu-id="44903-117">Bu örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44903-117">Examples of these are:</span></span>  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>  
  
<a name="implicit_use"></a>   
## <a name="implicit-use"></a><span data-ttu-id="44903-118">Örtük kullanın</span><span class="sxs-lookup"><span data-stu-id="44903-118">Implicit Use</span></span>  
 <span data-ttu-id="44903-119">Yükleme birkaç derleme ürettiği hataları örtük kendi CA ilke kullanımı nedeniyle overloads.</span><span class="sxs-lookup"><span data-stu-id="44903-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="44903-120">Bu aşırı ele bir <xref:System.Security.Policy.Evidence> CAS ilkesini çözümlemek ve izin sağlamak için kullanılan parametre kümesi bir derlemenin verin.</span><span class="sxs-lookup"><span data-stu-id="44903-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>  
  
 <span data-ttu-id="44903-121">İşte bazı örnekler.</span><span class="sxs-lookup"><span data-stu-id="44903-121">Here are some examples.</span></span> <span data-ttu-id="44903-122">Uygulamanız artık kullanılmayan aşırı dosyalardır <xref:System.Security.Policy.Evidence> bir parametre olarak:</span><span class="sxs-lookup"><span data-stu-id="44903-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
<a name="errors_and_warnings"></a>   
## <a name="errors-and-warnings"></a><span data-ttu-id="44903-123">Hatalar ve uyarılar</span><span class="sxs-lookup"><span data-stu-id="44903-123">Errors and Warnings</span></span>  
 <span data-ttu-id="44903-124">Bunların ne zaman kullanıldığını eski türler ve üyeleri aşağıdaki hata iletilerinden üretir.</span><span class="sxs-lookup"><span data-stu-id="44903-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="44903-125">Unutmayın <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> kendisini türü artık kullanılmayan değil.</span><span class="sxs-lookup"><span data-stu-id="44903-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>  
  
 <span data-ttu-id="44903-126">Derleme zamanı Uyarı:</span><span class="sxs-lookup"><span data-stu-id="44903-126">Compile-time warning:</span></span>  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 <span data-ttu-id="44903-127">Çalışma zamanı özel durum:</span><span class="sxs-lookup"><span data-stu-id="44903-127">Run-time exception:</span></span>  
  
 <span data-ttu-id="44903-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="44903-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="44903-129">Geçiş: Artık kullanılmayan çağrıları değiştirme</span><span class="sxs-lookup"><span data-stu-id="44903-129">Migration: Replacement for Obsolete Calls</span></span>  
  
### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="44903-130">Bir derlemenin güven düzeyini belirleme</span><span class="sxs-lookup"><span data-stu-id="44903-130">Determining an Assembly’s Trust Level</span></span>  
 <span data-ttu-id="44903-131">CA ilke genellikle bir derlemenin belirlemek için kullanılan veya uygulama etki alanının izin kümesi vermek veya güven düzeyi.</span><span class="sxs-lookup"><span data-stu-id="44903-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="44903-132">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Güvenlik ilkesi çözmek zorunda kalmazsınız aşağıdaki yararlı özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="44903-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a><span data-ttu-id="44903-133">Uygulama etki alanı korumalı alan</span><span class="sxs-lookup"><span data-stu-id="44903-133">Application Domain Sandboxing</span></span>  
 <span data-ttu-id="44903-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Yöntemdir genellikle uygulama etki alanı derlemelerde korumalı alan için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44903-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="44903-135">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Kullanmak zorunda değilsiniz üyeleri ortaya koyar <xref:System.Security.Policy.PolicyLevel> bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="44903-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="44903-136">Daha fazla bilgi için bkz: [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="44903-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="44903-137">Güvenilir kod kısmen güvenli veya makul izni için Ayarla belirleme</span><span class="sxs-lookup"><span data-stu-id="44903-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>  
 <span data-ttu-id="44903-138">Ana bilgisayarlar genellikle barındırılan korumalı alan kodu için uygun izinler belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44903-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="44903-139">Önce [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS ilkesini sağlanan ile bunu yapmanın bir yolu <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44903-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="44903-140">Bir yedek olarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sağlar <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> yöntemi için sağlanan kanıt ayarlamak güvenli, standart bir izin verir.</span><span class="sxs-lookup"><span data-stu-id="44903-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="44903-141">Korumalı alan olmayan senaryolar: Derleme yüklerini aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="44903-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>  
 <span data-ttu-id="44903-142">Aksi takdirde derleme korumalı alan yerine, kullanılabilir değil parametrelerini kullanmak için bir derleme yük aşırı kullanmanın nedeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="44903-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="44903-143">İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], gerektirmez derleme yük overloads bir <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> nesnesi bir bu gibi bir durumda parametresi olarak <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, bu senaryoyu.</span><span class="sxs-lookup"><span data-stu-id="44903-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>  
  
 <span data-ttu-id="44903-144">Korumalı alan için bir derleme istiyorsanız kullanın <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="44903-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="44903-145">Uyumluluğu: CA ilke eski seçeneği kullanma</span><span class="sxs-lookup"><span data-stu-id="44903-145">Compatibility: Using the CAS Policy Legacy Option</span></span>  
 <span data-ttu-id="44903-146">[< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) bir işlem veya kitaplık eski CAS ilkesini kullandığını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="44903-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="44903-147">Bu öğe etkinleştirdiğinizde, ilke ve kanıt aşırı framework'ün önceki sürümlerinde olduğu gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="44903-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44903-148">Bir çalışma zamanı sürümü için CAS ilkesini değiştirme başka bir sürümü CAS ilkesini etkilemesini CA ilke davranışı bir çalışma zamanı sürümü temelinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="44903-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44903-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44903-149">See Also</span></span>  
 [<span data-ttu-id="44903-150">Nasıl yapılır: korumalı alanda kısmen güvenilen kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44903-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
