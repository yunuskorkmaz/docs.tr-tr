---
description: 'Hakkında daha fazla bilgi edinin: <securityTokenHandlerConfiguration>'
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 8c014d971d3e8cc640a3b7042e3a0266d902de7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698316"
---
# \<securityTokenHandlerConfiguration>

<span data-ttu-id="ca5f9-102">Belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-102">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="ca5f9-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca5f9-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca5f9-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca5f9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ca5f9-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca5f9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca5f9-106">Attributes</span></span>  
  
|<span data-ttu-id="ca5f9-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ca5f9-107">Attribute</span></span>|<span data-ttu-id="ca5f9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca5f9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca5f9-109">Savebootstrapbağlamı</span><span class="sxs-lookup"><span data-stu-id="ca5f9-109">saveBootstrapContext</span></span>|<span data-ttu-id="ca5f9-110">Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-110">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="ca5f9-111">Değer, öğe üzerinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda de ayarlanabilir `saveBootstrapContext` [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="ca5f9-111">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="ca5f9-112">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-112">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="ca5f9-113">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="ca5f9-113">maximumClockSkew</span></span>|<span data-ttu-id="ca5f9-114"><xref:System.TimeSpan>İzin verilen maksimum saat eğriliğini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-114">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="ca5f9-115">Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-115">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="ca5f9-116">Varsayılan değer 5 dakikadır, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="ca5f9-116">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="ca5f9-117">Değerlerin nasıl belirtilmesi hakkında daha fazla bilgi için <xref:System.TimeSpan> bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ca5f9-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="ca5f9-118">En büyük saat eğriltme, öğesinde özniteliği ayarlanarak de hizmet düzeyinde ayarlanabilir `maximumClockSkew` [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="ca5f9-118">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="ca5f9-119">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-119">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca5f9-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca5f9-120">Child Elements</span></span>  
  
|<span data-ttu-id="ca5f9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca5f9-121">Element</span></span>|<span data-ttu-id="ca5f9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca5f9-122">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="ca5f9-123">Bu bağlı olan tarafın kabul edilebilir tanımlayıcıları olan URI kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-123">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="ca5f9-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-124">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="ca5f9-125">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-125">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="ca5f9-126">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-126">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ca5f9-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-127">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="ca5f9-128">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-128">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="ca5f9-129">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-129">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ca5f9-130">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-130">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="ca5f9-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-131">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="ca5f9-132">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-132">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ca5f9-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-133">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="ca5f9-134">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-134">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ca5f9-135">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-135">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="ca5f9-136">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-136">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="ca5f9-137">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-137">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ca5f9-138">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-138">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="ca5f9-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-139">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="ca5f9-140">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-140">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="ca5f9-141">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-141">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ca5f9-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-142">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca5f9-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca5f9-143">Parent Elements</span></span>  
  
|<span data-ttu-id="ca5f9-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca5f9-144">Element</span></span>|<span data-ttu-id="ca5f9-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca5f9-145">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="ca5f9-146">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-146">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca5f9-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca5f9-147">Remarks</span></span>  

 <span data-ttu-id="ca5f9-148">Bu bölüm bir nesne için özellik değerleri sağlar <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> .</span><span class="sxs-lookup"><span data-stu-id="ca5f9-148">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="ca5f9-149">Bu bölümde yapılandırılan ayarlar, hizmette yapılandırılan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-149">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="ca5f9-150">Bu ayarlardan bazıları, güvenlik belirteci işleyici koleksiyonuna bir işleyici eklendiğinde belirtilen ayarlar tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ca5f9-150">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca5f9-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca5f9-151">Example</span></span>  
  
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
