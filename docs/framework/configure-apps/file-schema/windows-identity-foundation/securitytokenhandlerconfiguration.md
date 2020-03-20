---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152573"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="bad9f-101">\<güvenlikTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="bad9f-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="bad9f-102">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bad9f-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="bad9f-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bad9f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bad9f-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="bad9f-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="bad9f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="bad9f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="bad9f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="bad9f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="bad9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<güvenlikTokenHandlerConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="bad9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad9f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bad9f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bad9f-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bad9f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bad9f-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bad9f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bad9f-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bad9f-111">Attributes</span></span>  
  
|<span data-ttu-id="bad9f-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bad9f-112">Attribute</span></span>|<span data-ttu-id="bad9f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bad9f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bad9f-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="bad9f-114">saveBootstrapContext</span></span>|<span data-ttu-id="bad9f-115">Bootstrap belirteçlerinin oturum belirtecine dahil edilip edilmemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="bad9f-116">Değer, [ \<identityConfiguration>](identityconfiguration.md) öğesindeki özniteliği ayarlayarak `saveBootstrapContext` bir belirteç işleyicisi koleksiyonunda da ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="bad9f-117">Belirteç işleyicisi koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bad9f-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="bad9f-118">maksimumClockSkew</span><span class="sxs-lookup"><span data-stu-id="bad9f-118">maximumClockSkew</span></span>|<span data-ttu-id="bad9f-119">İzin <xref:System.TimeSpan> verilen maksimum saat eğriliğini belirten bir saat.</span><span class="sxs-lookup"><span data-stu-id="bad9f-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="bad9f-120">Oturum açma oturumunun son kullanma süresini doğrulamak gibi zamana duyarlı işlemleri gerçekleştirirken izin verilen maksimum saat eğriliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="bad9f-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="bad9f-121">Varsayılan değer 5 dakika, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="bad9f-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="bad9f-122">Değerleri nasıl belirtirim <xref:System.TimeSpan> hakkında daha fazla bilgi için [Timespan Değerleri'ne](../windows-workflow-foundation/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="bad9f-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="bad9f-123">Maksimum saat eğriliği, `maximumClockSkew` [ \<identityConfiguration>](identityconfiguration.md) öğesiözebiyi ayarlayarak hizmet düzeyinde de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="bad9f-124">Belirteç işleyicisi koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bad9f-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bad9f-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bad9f-125">Child Elements</span></span>  
  
|<span data-ttu-id="bad9f-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="bad9f-126">Element</span></span>|<span data-ttu-id="bad9f-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bad9f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bad9f-128">\<izleyiciUris></span><span class="sxs-lookup"><span data-stu-id="bad9f-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="bad9f-129">Bu güvenen tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="bad9f-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-130">Optional.</span></span>|  
|[<span data-ttu-id="bad9f-131">\<önbellekleri></span><span class="sxs-lookup"><span data-stu-id="bad9f-131">\<caches></span></span>](caches.md)|<span data-ttu-id="bad9f-132">Oturum belirteçleri ve belirteç yeniden algılamaiçin kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bad9f-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="bad9f-133">Hizmet düzeyinde veya güvenlik belirteç leri koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="bad9f-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-134">Optional.</span></span>|  
|[<span data-ttu-id="bad9f-135">\<sertifikaDoğrulama></span><span class="sxs-lookup"><span data-stu-id="bad9f-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="bad9f-136">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="bad9f-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="bad9f-137">Hizmet düzeyinde veya güvenlik belirteç leri koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="bad9f-138">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırılırsa, bu ayarlar geçersiz kılınur.</span><span class="sxs-lookup"><span data-stu-id="bad9f-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="bad9f-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-139">Optional.</span></span>|  
|[<span data-ttu-id="bad9f-140">\<verenNameRegistry></span><span class="sxs-lookup"><span data-stu-id="bad9f-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="bad9f-141">Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan veren ad kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bad9f-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="bad9f-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-142">Optional.</span></span>|  
|[<span data-ttu-id="bad9f-143">\<verenTokenResolver></span><span class="sxs-lookup"><span data-stu-id="bad9f-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="bad9f-144">Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bad9f-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="bad9f-145">Veren belirteç çözümleyici, gelen belirteçler ve iletiler üzerinde imza belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bad9f-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="bad9f-146">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-146">Optional.</span></span>|  
|[<span data-ttu-id="bad9f-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="bad9f-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="bad9f-148">Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bad9f-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="bad9f-149">Hizmet belirteci çözümleyicisi, gelen belirteçler ve iletiler üzerindeki şifreleme belirteci çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bad9f-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="bad9f-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-150">Optional.</span></span>|  
|[<span data-ttu-id="bad9f-151">\<tokenReplayAlgılama></span><span class="sxs-lookup"><span data-stu-id="bad9f-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="bad9f-152">Belirteç yeniden oynatma algılamasını sağlar ve belirteçlerin son kullanma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="bad9f-153">Hizmet düzeyinde veya güvenlik belirteç leri koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="bad9f-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bad9f-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bad9f-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bad9f-155">Parent Elements</span></span>  
  
|<span data-ttu-id="bad9f-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="bad9f-156">Element</span></span>|<span data-ttu-id="bad9f-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bad9f-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bad9f-158">\<güvenlikTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="bad9f-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="bad9f-159">Bitiş noktasına kayıtlı bir güvenlik belirteç işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad9f-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bad9f-160">Remarks</span></span>  
 <span data-ttu-id="bad9f-161">Bu bölümde bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne için özellik değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bad9f-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="bad9f-162">Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılanları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bad9f-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="bad9f-163">Bu ayarlardan bazıları, sırayla, güvenlik belirteci işleyicisi koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="bad9f-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bad9f-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="bad9f-164">Example</span></span>  
  
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
