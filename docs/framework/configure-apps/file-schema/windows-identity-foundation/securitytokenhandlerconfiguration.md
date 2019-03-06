---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 29e18cdda9e18addef4f0f32fd30e9abf6af78fc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360413"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="adc5c-101">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="adc5c-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="adc5c-102">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="adc5c-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="adc5c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="adc5c-103">\<system.identityModel></span></span>  
<span data-ttu-id="adc5c-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="adc5c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="adc5c-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="adc5c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="adc5c-106">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="adc5c-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc5c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adc5c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adc5c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="adc5c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="adc5c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="adc5c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adc5c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="adc5c-110">Attributes</span></span>  
  
|<span data-ttu-id="adc5c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="adc5c-111">Attribute</span></span>|<span data-ttu-id="adc5c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adc5c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adc5c-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="adc5c-113">saveBootstrapContext</span></span>|<span data-ttu-id="adc5c-114">Oturum belirteci önyükleme simgeleri dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="adc5c-115">Değer aynı zamanda bir belirteci işleyicisi koleksiyonunda ayarlayarak ayarlanabilir `saveBootstrapContext` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="adc5c-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="adc5c-116">Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="adc5c-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="adc5c-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="adc5c-117">maximumClockSkew</span></span>|<span data-ttu-id="adc5c-118">A <xref:System.TimeSpan> en fazla izin verilen saat sapması belirtir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="adc5c-119">Bir oturum açma oturumu sona erme süresini doğrulama gibi zamana duyarlı işlemleri gerçekleştirirken, en fazla izin verilen saat sapması denetler.</span><span class="sxs-lookup"><span data-stu-id="adc5c-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="adc5c-120">5 dakika, varsayılan değer "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="adc5c-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="adc5c-121">Belirtme hakkında daha fazla bilgi için <xref:System.TimeSpan> değerleri, görmek [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="adc5c-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="adc5c-122">Maksimum saat eğriltme da hizmet düzeyinde ayarlayarak ayarlanabilir `maximumClockSkew` özniteliği [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="adc5c-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="adc5c-123">Belirteci işleyicisi koleksiyonunda belirlenen bir değer hizmette ayarlanan değer geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="adc5c-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adc5c-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="adc5c-124">Child Elements</span></span>  
  
|<span data-ttu-id="adc5c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="adc5c-125">Element</span></span>|<span data-ttu-id="adc5c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adc5c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc5c-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="adc5c-127">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="adc5c-128">Bu bağlı olan tarafın tanımlayıcılardır kabul edilebilir bir URI'leri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="adc5c-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-129">Optional.</span></span>|  
|[<span data-ttu-id="adc5c-130">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="adc5c-130">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="adc5c-131">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="adc5c-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="adc5c-132">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="adc5c-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-133">Optional.</span></span>|  
|[<span data-ttu-id="adc5c-134">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="adc5c-134">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="adc5c-135">Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler.</span><span class="sxs-lookup"><span data-stu-id="adc5c-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="adc5c-136">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="adc5c-137">Belirli bir işleyici kendi Doğrulayıcı ile yapılandırılmışsa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="adc5c-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="adc5c-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-138">Optional.</span></span>|  
|[<span data-ttu-id="adc5c-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="adc5c-139">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="adc5c-140">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verenin ad Kayıt Defteri'ni yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="adc5c-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="adc5c-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-141">Optional.</span></span>|  
|[<span data-ttu-id="adc5c-142">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="adc5c-142">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="adc5c-143">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verici belirteç çözümleyici kaydeder.</span><span class="sxs-lookup"><span data-stu-id="adc5c-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="adc5c-144">Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="adc5c-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="adc5c-145">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-145">Optional.</span></span>|  
|[<span data-ttu-id="adc5c-146">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="adc5c-146">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="adc5c-147">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="adc5c-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="adc5c-148">Hizmet belirteç Çözümleyici, gelen belirteçleri ve ileti şifreleme belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="adc5c-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="adc5c-149">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-149">Optional.</span></span>|  
|[<span data-ttu-id="adc5c-150">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="adc5c-150">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="adc5c-151">Belirteç yeniden yürütme algılaması sağlar ve belirteçleri sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="adc5c-152">Hizmet düzeyinde veya bir güvenlik belirteci işleyicisi koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="adc5c-153">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="adc5c-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adc5c-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="adc5c-154">Parent Elements</span></span>  
  
|<span data-ttu-id="adc5c-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="adc5c-155">Element</span></span>|<span data-ttu-id="adc5c-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adc5c-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc5c-157">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="adc5c-157">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="adc5c-158">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc5c-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adc5c-159">Remarks</span></span>  
 <span data-ttu-id="adc5c-160">Özellik değerleri için bu bölümde bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne.</span><span class="sxs-lookup"><span data-stu-id="adc5c-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="adc5c-161">Bu bölümde, yapılandırılan ayarları hizmetinde yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="adc5c-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="adc5c-162">Bu ayarlardan bazıları sırasıyla bir işleyici güvenlik belirteci işleyicisi koleksiyona eklendiğinde, belirtilen ayarları tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="adc5c-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adc5c-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="adc5c-163">Example</span></span>  
  
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
