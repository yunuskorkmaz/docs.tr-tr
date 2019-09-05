---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251882"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="ea9df-101">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ea9df-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="ea9df-102">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea9df-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="ea9df-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea9df-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea9df-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ea9df-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ea9df-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ea9df-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ea9df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="ea9df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="ea9df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="ea9df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea9df-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea9df-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea9df-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea9df-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ea9df-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea9df-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea9df-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea9df-111">Attributes</span></span>  
  
|<span data-ttu-id="ea9df-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea9df-112">Attribute</span></span>|<span data-ttu-id="ea9df-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea9df-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea9df-114">Savebootstrapbağlamı</span><span class="sxs-lookup"><span data-stu-id="ea9df-114">saveBootstrapContext</span></span>|<span data-ttu-id="ea9df-115">Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="ea9df-116">Ayrıca, `saveBootstrapContext` [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda değer de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="ea9df-117">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ea9df-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="ea9df-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="ea9df-118">maximumClockSkew</span></span>|<span data-ttu-id="ea9df-119">İzin <xref:System.TimeSpan> verilen maksimum saat eğriliğini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="ea9df-120">Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="ea9df-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="ea9df-121">Varsayılan değer 5 dakikadır, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="ea9df-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="ea9df-122">Değerlerin nasıl belirtilmesi <xref:System.TimeSpan> hakkında daha fazla bilgi için bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea9df-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="ea9df-123">Ayrıca, `maximumClockSkew` [ \<IdentityConfiguration >](identityconfiguration.md) öğesinde özniteliği ayarlanarak hizmet düzeyinde maksimum saat eğriltme de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="ea9df-124">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ea9df-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea9df-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea9df-125">Child Elements</span></span>  
  
|<span data-ttu-id="ea9df-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea9df-126">Element</span></span>|<span data-ttu-id="ea9df-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea9df-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea9df-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="ea9df-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="ea9df-129">Bu bağlı olan tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="ea9df-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-130">Optional.</span></span>|  
|[<span data-ttu-id="ea9df-131">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="ea9df-131">\<caches></span></span>](caches.md)|<span data-ttu-id="ea9df-132">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ea9df-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="ea9df-133">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ea9df-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-134">Optional.</span></span>|  
|[<span data-ttu-id="ea9df-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="ea9df-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="ea9df-136">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="ea9df-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="ea9df-137">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ea9df-138">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="ea9df-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="ea9df-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-139">Optional.</span></span>|  
|[<span data-ttu-id="ea9df-140">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="ea9df-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="ea9df-141">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ea9df-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ea9df-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-142">Optional.</span></span>|  
|[<span data-ttu-id="ea9df-143">\<IssuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="ea9df-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="ea9df-144">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ea9df-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ea9df-145">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea9df-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="ea9df-146">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-146">Optional.</span></span>|  
|[<span data-ttu-id="ea9df-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="ea9df-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="ea9df-148">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ea9df-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ea9df-149">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea9df-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="ea9df-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-150">Optional.</span></span>|  
|[<span data-ttu-id="ea9df-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="ea9df-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="ea9df-152">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="ea9df-153">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ea9df-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea9df-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea9df-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea9df-155">Parent Elements</span></span>  
  
|<span data-ttu-id="ea9df-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea9df-156">Element</span></span>|<span data-ttu-id="ea9df-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea9df-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea9df-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="ea9df-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="ea9df-159">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea9df-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea9df-160">Remarks</span></span>  
 <span data-ttu-id="ea9df-161">Bu bölüm bir <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> nesne için özellik değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea9df-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="ea9df-162">Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ea9df-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="ea9df-163">Bu ayarlardan bazıları, güvenlik belirteci işleyici koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ea9df-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea9df-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea9df-164">Example</span></span>  
  
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
