---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942453"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="60c2b-101">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60c2b-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="60c2b-102">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c2b-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="60c2b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="60c2b-103">\<system.identityModel></span></span>  
<span data-ttu-id="60c2b-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60c2b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="60c2b-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="60c2b-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="60c2b-106">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60c2b-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c2b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60c2b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60c2b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60c2b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="60c2b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60c2b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60c2b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60c2b-110">Attributes</span></span>  
  
|<span data-ttu-id="60c2b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60c2b-111">Attribute</span></span>|<span data-ttu-id="60c2b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60c2b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60c2b-113">Savebootstrapbağlamı</span><span class="sxs-lookup"><span data-stu-id="60c2b-113">saveBootstrapContext</span></span>|<span data-ttu-id="60c2b-114">Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="60c2b-115">Ayrıca, `saveBootstrapContext` [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda değer de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="60c2b-116">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60c2b-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="60c2b-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="60c2b-117">maximumClockSkew</span></span>|<span data-ttu-id="60c2b-118">İzin <xref:System.TimeSpan> verilen maksimum saat eğriliğini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="60c2b-119">Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="60c2b-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="60c2b-120">Varsayılan değer 5 dakikadır, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="60c2b-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="60c2b-121">Değerlerin nasıl belirtilmesi <xref:System.TimeSpan> hakkında daha fazla bilgi için bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="60c2b-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="60c2b-122">Ayrıca, `maximumClockSkew` [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde özniteliği ayarlanarak hizmet düzeyinde maksimum saat eğriltme de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="60c2b-123">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60c2b-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60c2b-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60c2b-124">Child Elements</span></span>  
  
|<span data-ttu-id="60c2b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="60c2b-125">Element</span></span>|<span data-ttu-id="60c2b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60c2b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60c2b-127">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="60c2b-127">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="60c2b-128">Bu bağlı olan tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="60c2b-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-129">Optional.</span></span>|  
|[<span data-ttu-id="60c2b-130">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="60c2b-130">\<caches></span></span>](caches.md)|<span data-ttu-id="60c2b-131">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60c2b-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="60c2b-132">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="60c2b-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-133">Optional.</span></span>|  
|[<span data-ttu-id="60c2b-134">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="60c2b-134">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="60c2b-135">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="60c2b-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="60c2b-136">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="60c2b-137">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="60c2b-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="60c2b-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-138">Optional.</span></span>|  
|[<span data-ttu-id="60c2b-139">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="60c2b-139">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="60c2b-140">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="60c2b-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="60c2b-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-141">Optional.</span></span>|  
|[<span data-ttu-id="60c2b-142">\<IssuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="60c2b-142">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="60c2b-143">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60c2b-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="60c2b-144">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60c2b-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="60c2b-145">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-145">Optional.</span></span>|  
|[<span data-ttu-id="60c2b-146">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="60c2b-146">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="60c2b-147">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60c2b-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="60c2b-148">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60c2b-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="60c2b-149">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-149">Optional.</span></span>|  
|[<span data-ttu-id="60c2b-150">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="60c2b-150">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="60c2b-151">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="60c2b-152">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="60c2b-153">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60c2b-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60c2b-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60c2b-154">Parent Elements</span></span>  
  
|<span data-ttu-id="60c2b-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="60c2b-155">Element</span></span>|<span data-ttu-id="60c2b-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60c2b-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60c2b-157">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="60c2b-157">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="60c2b-158">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60c2b-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60c2b-159">Remarks</span></span>  
 <span data-ttu-id="60c2b-160">Bu bölüm bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne için özellik değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c2b-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="60c2b-161">Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60c2b-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="60c2b-162">Bu ayarlardan bazıları, güvenlik belirteci işleyici koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="60c2b-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60c2b-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="60c2b-163">Example</span></span>  
  
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
