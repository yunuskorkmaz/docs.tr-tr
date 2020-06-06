---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152573"
---
# \<securityTokenHandlerConfiguration>
<span data-ttu-id="60716-101">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="60716-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="60716-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60716-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60716-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60716-103">Attributes and Elements</span></span>  
 <span data-ttu-id="60716-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60716-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60716-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60716-105">Attributes</span></span>  
  
|<span data-ttu-id="60716-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60716-106">Attribute</span></span>|<span data-ttu-id="60716-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60716-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60716-108">Savebootstrapbağlamı</span><span class="sxs-lookup"><span data-stu-id="60716-108">saveBootstrapContext</span></span>|<span data-ttu-id="60716-109">Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60716-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="60716-110">Değer, öğe üzerinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda de ayarlanabilir `saveBootstrapContext` [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="60716-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="60716-111">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60716-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="60716-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="60716-112">maximumClockSkew</span></span>|<span data-ttu-id="60716-113"><xref:System.TimeSpan>İzin verilen maksimum saat eğriliğini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="60716-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="60716-114">Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="60716-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="60716-115">Varsayılan değer 5 dakikadır, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="60716-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="60716-116">Değerlerin nasıl belirtilmesi hakkında daha fazla bilgi için <xref:System.TimeSpan> bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="60716-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="60716-117">En büyük saat eğriltme, öğesinde özniteliği ayarlanarak de hizmet düzeyinde ayarlanabilir `maximumClockSkew` [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="60716-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="60716-118">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60716-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60716-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60716-119">Child Elements</span></span>  
  
|<span data-ttu-id="60716-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="60716-120">Element</span></span>|<span data-ttu-id="60716-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60716-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="60716-122">Bu bağlı olan tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60716-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="60716-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="60716-124">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60716-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="60716-125">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="60716-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="60716-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="60716-127">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="60716-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="60716-128">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="60716-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="60716-129">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="60716-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="60716-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="60716-131">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="60716-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="60716-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="60716-133">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60716-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="60716-134">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60716-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="60716-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="60716-136">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60716-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="60716-137">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60716-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="60716-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="60716-139">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60716-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="60716-140">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="60716-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="60716-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="60716-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60716-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60716-142">Parent Elements</span></span>  
  
|<span data-ttu-id="60716-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="60716-143">Element</span></span>|<span data-ttu-id="60716-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60716-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="60716-145">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="60716-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60716-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60716-146">Remarks</span></span>  
 <span data-ttu-id="60716-147">Bu bölüm bir nesne için özellik değerleri sağlar <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> .</span><span class="sxs-lookup"><span data-stu-id="60716-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="60716-148">Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60716-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="60716-149">Bu ayarlardan bazıları, güvenlik belirteci işleyici koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="60716-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60716-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="60716-150">Example</span></span>  
  
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
