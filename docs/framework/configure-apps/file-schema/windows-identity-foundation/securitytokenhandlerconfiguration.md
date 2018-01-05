---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ac7284fa418c1540582c40bd744e913ba31aa881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="e2797-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="e2797-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="e2797-103">Belirteç işleyicileri koleksiyonunu yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2797-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="e2797-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="e2797-104">\<system.identityModel></span></span>  
<span data-ttu-id="e2797-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e2797-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e2797-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e2797-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e2797-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e2797-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2797-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2797-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2797-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2797-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e2797-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2797-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2797-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2797-111">Attributes</span></span>  
  
|<span data-ttu-id="e2797-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2797-112">Attribute</span></span>|<span data-ttu-id="e2797-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2797-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2797-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="e2797-114">saveBootstrapContext</span></span>|<span data-ttu-id="e2797-115">Oturum belirteci önyükleme belirteçlerini dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2797-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="e2797-116">Değer ayrıca bir belirteç işleyici koleksiyonu ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="e2797-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="e2797-117">Bir değer belirteci işleyicisi koleksiyonda Ayarla hizmetinde değerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e2797-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="e2797-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="e2797-118">maximumClockSkew</span></span>|<span data-ttu-id="e2797-119">A <xref:System.TimeSpan> izin verilen maksimum saat eğriltme belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2797-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="e2797-120">İzin verilen maksimum saat eğriltme bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemlerini gerçekleştirirken denetler.</span><span class="sxs-lookup"><span data-stu-id="e2797-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="e2797-121">5 dakika, varsayılan değer "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="e2797-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="e2797-122">Nasıl belirleneceği hakkında daha fazla bilgi için <xref:System.TimeSpan> değerler, bakın [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2797-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="e2797-123">Maksimum saat eğriltme Ayrıca hizmet düzeyinde ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="e2797-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="e2797-124">Bir değer belirteci işleyicisi koleksiyonda Ayarla hizmetinde değerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e2797-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2797-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2797-125">Child Elements</span></span>  
  
|<span data-ttu-id="e2797-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2797-126">Element</span></span>|<span data-ttu-id="e2797-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2797-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2797-128">\<AudienceUri ></span><span class="sxs-lookup"><span data-stu-id="e2797-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="e2797-129">Bu bağlı olan taraf kabul edilebilir tanımlayıcılardır URI'ler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2797-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="e2797-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-130">Optional.</span></span>|  
|[<span data-ttu-id="e2797-131">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="e2797-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="e2797-132">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2797-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="e2797-133">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e2797-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e2797-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-134">Optional.</span></span>|  
|[<span data-ttu-id="e2797-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="e2797-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="e2797-136">Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="e2797-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e2797-137">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e2797-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e2797-138">Belirli bir işleyici ile kendi Doğrulayıcı yapılandırdıysanız bu ayarları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="e2797-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="e2797-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-139">Optional.</span></span>|  
|[<span data-ttu-id="e2797-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="e2797-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="e2797-141">Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan yayınlayıcı adı kaydını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e2797-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e2797-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-142">Optional.</span></span>|  
|[<span data-ttu-id="e2797-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e2797-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="e2797-144">Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan veren belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2797-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e2797-145">Veren belirteç Çözümleyicisi gelen iletileri ve belirteç imzalama belirteçte çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2797-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="e2797-146">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-146">Optional.</span></span>|  
|[<span data-ttu-id="e2797-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e2797-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="e2797-148">Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2797-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e2797-149">Hizmet belirteç Çözümleyicisi gelen belirteçleri ve iletileri şifreleme belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2797-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e2797-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-150">Optional.</span></span>|  
|[<span data-ttu-id="e2797-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="e2797-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="e2797-152">Belirteç yeniden yürütme algılaması sağlar ve belirteçler için sona erme saati belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2797-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="e2797-153">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e2797-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e2797-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e2797-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2797-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2797-155">Parent Elements</span></span>  
  
|<span data-ttu-id="e2797-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2797-156">Element</span></span>|<span data-ttu-id="e2797-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2797-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2797-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e2797-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="e2797-159">Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2797-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2797-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2797-160">Remarks</span></span>  
 <span data-ttu-id="e2797-161">Bu bölüm için özellik değerlerini sağlayan bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e2797-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="e2797-162">Bu bölümde yapılandırılan ayarları hizmetinde yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e2797-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="e2797-163">Bu ayarlardan bazıları sırayla, güvenlik belirteci işleyicisi koleksiyonuna bir işleyici eklediğinizde, belirtilen ayarlarla geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="e2797-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2797-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2797-164">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
