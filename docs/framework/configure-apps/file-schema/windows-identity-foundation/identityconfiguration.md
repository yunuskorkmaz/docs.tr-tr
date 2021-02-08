---
description: 'Hakkında daha fazla bilgi edinin: <identityConfiguration>'
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 987dfb006984f757ad117157e915f1909ab3a8c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773413"
---
# \<identityConfiguration>

<span data-ttu-id="19798-102">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-102">Specifies service-level identity settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

## <a name="syntax"></a><span data-ttu-id="19798-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="19798-103">Syntax</span></span>

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19798-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19798-104">Attributes and Elements</span></span>

<span data-ttu-id="19798-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19798-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="19798-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19798-106">Attributes</span></span>

|<span data-ttu-id="19798-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19798-107">Attribute</span></span>|<span data-ttu-id="19798-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19798-108">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="19798-109">name</span><span class="sxs-lookup"><span data-stu-id="19798-109">name</span></span>|<span data-ttu-id="19798-110">Kimlik yapılandırma bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="19798-110">The name of the identity configuration section.</span></span> <span data-ttu-id="19798-111">Bu adı, belirli bir yapılandırma bölümüne başvurmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19798-111">You can use this name to reference a specific configuration section.</span></span> <span data-ttu-id="19798-112">Hiçbir `name` öznitelik belirtilmemişse, Bölüm varsayılan yapılandırmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="19798-112">If no `name` attribute is specified, the section defines the default configuration.</span></span> <span data-ttu-id="19798-113">Varsayılan yapılandırma, Pasif Federasyon senaryolarında her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19798-113">The default configuration is always used for passive federation scenarios.</span></span> <span data-ttu-id="19798-114">Daha fazla bilgi için, bkz [\<federationConfiguration>](federationconfiguration.md) . öğesi.</span><span class="sxs-lookup"><span data-stu-id="19798-114">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>|
|<span data-ttu-id="19798-115">Savebootstrapbağlamı</span><span class="sxs-lookup"><span data-stu-id="19798-115">saveBootstrapContext</span></span>|<span data-ttu-id="19798-116">Önyükleme belirteçlerinin oturum belirtecine dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-116">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="19798-117">Değer, öğe üzerinde özniteliği ayarlanarak bir belirteç işleyici koleksiyonunda de ayarlanabilir `saveBootstrapContext` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="19798-117">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="19798-118">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="19798-118">A value set on the token handler collection overrides the value set on the service.</span></span>|
|<span data-ttu-id="19798-119">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="19798-119">maximumClockSkew</span></span>|<span data-ttu-id="19798-120"><xref:System.TimeSpan>İzin verilen maksimum saat eğriliğini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="19798-120">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="19798-121">Oturum açma oturumunun sona erme süresini doğrulamak gibi zamana duyarlı işlemler gerçekleştirirken izin verilen maksimum saat eğriliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="19798-121">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="19798-122">Varsayılan değer 5 dakikadır, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="19798-122">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="19798-123">Değerlerin nasıl belirtilmesi hakkında daha fazla bilgi için <xref:System.TimeSpan> bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="19798-123">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="19798-124">Öğe üzerinde özniteliği ayarlanarak, bir belirteç işleyici koleksiyonunda maksimum saat eğriltme de ayarlanabilir `maximumClockSkew` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="19798-124">The maximum clock skew may also be set on a token handler collection by setting the `maximumClockSkew` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="19798-125">Belirteç işleyici koleksiyonunda ayarlanan değer, hizmette ayarlanan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="19798-125">A value set on the token handler collection overrides the value set on the service.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="19798-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19798-126">Child Elements</span></span>

|<span data-ttu-id="19798-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="19798-127">Element</span></span>|<span data-ttu-id="19798-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19798-128">Description</span></span>|
|-------------|-----------------|
|[\<caches>](caches.md)|<span data-ttu-id="19798-129">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="19798-129">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="19798-130">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="19798-130">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="19798-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-131">Optional.</span></span>|
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="19798-132">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="19798-132">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="19798-133">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="19798-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="19798-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-134">Optional.</span></span>|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|<span data-ttu-id="19798-135">Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="19798-135">Registers a claims authentication manager for the incoming claims.</span></span> <span data-ttu-id="19798-136">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-136">Optional.</span></span>|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|<span data-ttu-id="19798-137">Gelen talepler için bir talep Yetkilendirme Yöneticisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="19798-137">Registers a claims authorization manager for the incoming claims.</span></span> <span data-ttu-id="19798-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-138">Optional.</span></span>|
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="19798-139">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-139">Specifies the set of required claims for incoming security tokens.</span></span> <span data-ttu-id="19798-140">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-140">Optional.</span></span>|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="19798-141">Bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-141">Specifies a collection of security token handlers.</span></span> <span data-ttu-id="19798-142">Sıfır veya daha fazla güvenlik belirteci işleyicisi koleksiyonu belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="19798-142">Zero or more collections of security token handlers can be specified.</span></span> <span data-ttu-id="19798-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-143">Optional.</span></span>|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="19798-144">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-144">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="19798-145">, Hizmet düzeyinde veya bir güvenlik belirteci işleyici koleksiyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="19798-145">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="19798-146">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19798-146">Optional.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="19798-147">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19798-147">Parent Elements</span></span>

|<span data-ttu-id="19798-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="19798-148">Element</span></span>|<span data-ttu-id="19798-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19798-149">Description</span></span>|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|<span data-ttu-id="19798-150">Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="19798-150">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="19798-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19798-151">Remarks</span></span>

<span data-ttu-id="19798-152">Her biri benzersiz bir ada sahip birden çok kimlik yapılandırması tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="19798-152">Multiple identity configurations may be defined, each with a unique name.</span></span> <span data-ttu-id="19798-153">Davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="19798-153">The behavior is as follows:</span></span>

1. <span data-ttu-id="19798-154">Eğer hiçbir `<identityConfiguration>` öğe belirtilmemişse.</span><span class="sxs-lookup"><span data-stu-id="19798-154">If no `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="19798-155">Çalışma zamanında varsayılan bir kimlik yapılandırması oluşturulur ve varsayılan değerlerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="19798-155">A default identity configuration is created at runtime and populated with default values.</span></span>

2. <span data-ttu-id="19798-156">Tek bir `<identityConfiguration>` öğe belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="19798-156">If a single `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="19798-157">Varsayılan kimlik yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="19798-157">It is the default identity configuration.</span></span> <span data-ttu-id="19798-158">Adlandırılmış veya adlandırılmamış bir önemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="19798-158">It does not matter whether it is named or unnamed.</span></span>

3. <span data-ttu-id="19798-159">Birden çok `<identityConfiguration>` öğe belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="19798-159">If multiple `<identityConfiguration>` elements are specified.</span></span> <span data-ttu-id="19798-160">Adlandırılmamış öğe varsayılan kimlik yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-160">The unnamed element specifies the default identity configuration.</span></span> <span data-ttu-id="19798-161">Birden çok `<identityConfiguration>` öğe belirttiğinizde, bunlardan birinin adlandırılmamış olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="19798-161">It is recommended that when you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span>

> [!WARNING]
> <span data-ttu-id="19798-162">Birden çok öğe belirtirseniz `<identityConfiguration>` , bunlardan biri adlandırılmamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19798-162">If you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span> <span data-ttu-id="19798-163">Adlandırılmamış öğe varsayılan kimlik yapılandırması olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19798-163">The unnamed element will be the default identity configuration.</span></span>

 <span data-ttu-id="19798-164">Öğesinde belirtilen ayarlardan bazıları `<identityConfiguration>` bir güvenlik belirteci işleyici koleksiyonundaki ayarlar veya ayrı güvenlik belirteci işleyicilerindeki ayarlar tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="19798-164">Some of the settings specified in the `<identityConfiguration>` element can be overridden by settings on a security token handler collection or by settings on individual security token handlers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19798-165"><xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, öğesinin başvurduğu kimlik yapılandırması, `<federationConfiguration>` yetkilendirme kararları vermek için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="19798-165">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="19798-166">Bu, pasif Web senaryoları olmayan senaryolarda bile, örneğin Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19798-166">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="19798-167">Uygulama pasif bir Web uygulaması değilse, [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) uygulanan tek ayarlardır.</span><span class="sxs-lookup"><span data-stu-id="19798-167">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="19798-168">Diğer tüm ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="19798-168">All other settings are ignored.</span></span> <span data-ttu-id="19798-169">Daha fazla bilgi için, bkz [\<federationConfiguration>](federationconfiguration.md) . öğesi.</span><span class="sxs-lookup"><span data-stu-id="19798-169">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>

<span data-ttu-id="19798-170">`<identityConfiguration>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> .</span><span class="sxs-lookup"><span data-stu-id="19798-170">The `<identityConfiguration>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> class.</span></span> <span data-ttu-id="19798-171">Bir kimlik yapılandırma bölümü sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityConfiguration> .</span><span class="sxs-lookup"><span data-stu-id="19798-171">An identity configuration section is represented by the <xref:System.IdentityModel.Configuration.IdentityConfiguration> class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19798-172">Aşağıdaki öğeleri öğesinin alt öğeleri olarak belirtmek `<identityConfiguration>` kullanım dışı bırakılmıştır, ancak davranış geriye dönük uyumluluk için hala desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19798-172">Specifying the following elements as child elements of the `<identityConfiguration>` element has been deprecated, although the behavior is still supported for backward compatibility.</span></span> <span data-ttu-id="19798-173">Bu öğeler, bunun yerine öğesi altında belirtilmelidir [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="19798-173">These elements should, instead, be specified under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span>
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a><span data-ttu-id="19798-174">Örnek</span><span class="sxs-lookup"><span data-stu-id="19798-174">Example</span></span>

<span data-ttu-id="19798-175">Aşağıdaki örnek, "alternateConfiguration" adlı bir kimlik yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19798-175">The following example creates an identity configuration named "alternateConfiguration".</span></span> <span data-ttu-id="19798-176">Kimlik yapılandırması varsayılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="19798-176">The identity configuration specifies default settings.</span></span>

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a><span data-ttu-id="19798-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19798-177">See also</span></span>

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
