---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793285"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="57a1b-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="57a1b-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="57a1b-103">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="57a1b-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="57a1b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="57a1b-104">\<system.identityModel></span></span>  
<span data-ttu-id="57a1b-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="57a1b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="57a1b-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="57a1b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="57a1b-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="57a1b-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a1b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57a1b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57a1b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57a1b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="57a1b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57a1b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57a1b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57a1b-111">Attributes</span></span>  
  
|<span data-ttu-id="57a1b-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57a1b-112">Attribute</span></span>|<span data-ttu-id="57a1b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57a1b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57a1b-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="57a1b-114">saveBootstrapContext</span></span>|<span data-ttu-id="57a1b-115">Oturum belirteci önyükleme simgeleri dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="57a1b-116">Değer aynı zamanda bir belirteci işleyicisi koleksiyonunda ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="57a1b-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="57a1b-117">Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="57a1b-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="57a1b-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="57a1b-118">maximumClockSkew</span></span>|<span data-ttu-id="57a1b-119">A <xref:System.TimeSpan> en fazla izin verilen saat sapması belirtir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="57a1b-120">Bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemleri gerçekleştirirken, en fazla izin verilen saat sapması denetler.</span><span class="sxs-lookup"><span data-stu-id="57a1b-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="57a1b-121">5 dakika, varsayılan değer "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="57a1b-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="57a1b-122">Belirtme hakkında daha fazla bilgi için <xref:System.TimeSpan> değerleri, görmek [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="57a1b-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="57a1b-123">Maksimum saat eğriltme da hizmet düzeyinde ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="57a1b-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="57a1b-124">Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="57a1b-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57a1b-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57a1b-125">Child Elements</span></span>  
  
|<span data-ttu-id="57a1b-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="57a1b-126">Element</span></span>|<span data-ttu-id="57a1b-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57a1b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57a1b-128">\<AudienceUri ></span><span class="sxs-lookup"><span data-stu-id="57a1b-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="57a1b-129">Bu bağlı olan tarafın tanımlayıcılardır kabul edilebilir bir URI'leri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="57a1b-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-130">Optional.</span></span>|  
|[<span data-ttu-id="57a1b-131">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="57a1b-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="57a1b-132">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57a1b-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="57a1b-133">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="57a1b-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-134">Optional.</span></span>|  
|[<span data-ttu-id="57a1b-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="57a1b-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="57a1b-136">Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler.</span><span class="sxs-lookup"><span data-stu-id="57a1b-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="57a1b-137">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="57a1b-138">Belirli bir işleyici kendi Doğrulayıcı ile yapılandırılmışsa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="57a1b-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="57a1b-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-139">Optional.</span></span>|  
|[<span data-ttu-id="57a1b-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="57a1b-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="57a1b-141">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verenin ad Kayıt Defteri'ni yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="57a1b-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="57a1b-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-142">Optional.</span></span>|  
|[<span data-ttu-id="57a1b-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="57a1b-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="57a1b-144">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verici belirteç çözümleyici kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57a1b-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="57a1b-145">Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57a1b-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="57a1b-146">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-146">Optional.</span></span>|  
|[<span data-ttu-id="57a1b-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="57a1b-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="57a1b-148">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57a1b-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="57a1b-149">Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57a1b-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="57a1b-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-150">Optional.</span></span>|  
|[<span data-ttu-id="57a1b-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="57a1b-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="57a1b-152">Belirteç yeniden yürütme algılaması sağlar ve belirteçleri sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="57a1b-153">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="57a1b-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="57a1b-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57a1b-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57a1b-155">Parent Elements</span></span>  
  
|<span data-ttu-id="57a1b-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="57a1b-156">Element</span></span>|<span data-ttu-id="57a1b-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57a1b-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57a1b-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="57a1b-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="57a1b-159">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57a1b-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57a1b-160">Remarks</span></span>  
 <span data-ttu-id="57a1b-161">Özellik değerleri için bu bölümde bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne.</span><span class="sxs-lookup"><span data-stu-id="57a1b-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="57a1b-162">Bu bölümde, yapılandırılan ayarları hizmetinde yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="57a1b-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="57a1b-163">Bu ayarlardan bazıları sırasıyla bir işleyici güvenlik belirteci işleyicisi koleksiyona eklendiğinde, belirtilen ayarları tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="57a1b-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57a1b-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="57a1b-164">Example</span></span>  
  
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
