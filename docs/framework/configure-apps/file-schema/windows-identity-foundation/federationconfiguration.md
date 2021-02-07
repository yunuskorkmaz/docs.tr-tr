---
description: 'Hakkında daha fazla bilgi edinin: <federationConfiguration>'
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: f8793a8fbd6fc6d5e6994c8e368f587b740e5973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748992"
---
# \<federationConfiguration>

<span data-ttu-id="c25fa-102"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> WS-Federation protokolü aracılığıyla federal kimlik doğrulaması kullanırken (wsfab) ve (Sam) öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-102">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="c25fa-103"><xref:System.Security.Claims.ClaimsAuthorizationManager> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-103">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="c25fa-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c25fa-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c25fa-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c25fa-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c25fa-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c25fa-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c25fa-107">Attributes</span></span>  
  
|<span data-ttu-id="c25fa-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c25fa-108">Attribute</span></span>|<span data-ttu-id="c25fa-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c25fa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c25fa-110">name</span><span class="sxs-lookup"><span data-stu-id="c25fa-110">name</span></span>|<span data-ttu-id="c25fa-111">Bu Federasyon yapılandırma öğesinin adı.</span><span class="sxs-lookup"><span data-stu-id="c25fa-111">The name of this federation configuration element.</span></span> <span data-ttu-id="c25fa-112">Bu öznitelik, öncelikle gelecekteki protokoller için bir genişletilebilirlik noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="c25fa-112">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="c25fa-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fa-113">Optional.</span></span>|  
|<span data-ttu-id="c25fa-114">ıdentityconfigurationname</span><span class="sxs-lookup"><span data-stu-id="c25fa-114">identityConfigurationName</span></span>|<span data-ttu-id="c25fa-115">Kullanılacak bir öğede belirtilen kimlik yapılandırma bölümünün adı [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="c25fa-115">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="c25fa-116">Bu öznitelik belirtilmemişse, varsayılan kimlik yapılandırma bölümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-116">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="c25fa-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fa-117">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c25fa-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c25fa-118">Child Elements</span></span>  
  
|<span data-ttu-id="c25fa-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c25fa-119">Element</span></span>|<span data-ttu-id="c25fa-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c25fa-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="c25fa-121">SAM tarafından kullanılan tanımlama bilgisi işleyicisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-121">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="c25fa-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fa-122">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="c25fa-123">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-123">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="c25fa-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fa-124">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="c25fa-125">WS-Federation kimlik doğrulama modülünü (WSFAD) yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-125">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="c25fa-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fa-126">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c25fa-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c25fa-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c25fa-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="c25fa-128">Element</span></span>|<span data-ttu-id="c25fa-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c25fa-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="c25fa-130">WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="c25fa-130">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c25fa-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c25fa-131">Remarks</span></span>  

 <span data-ttu-id="c25fa-132">\<federationConfiguration>Öğesi iki farklı senaryoda ayarlar sağlar:</span><span class="sxs-lookup"><span data-stu-id="c25fa-132">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="c25fa-133">Pasif bir Web uygulamasında WS-Federation kullanırken, öğesi <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (wsfab) ve (Sam) öğesini yapılandıran ayarları içerir <xref:System.IdentityModel.Services.SessionAuthenticationModule> .</span><span class="sxs-lookup"><span data-stu-id="c25fa-133">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="c25fa-134">Ayrıca güvenlik belirteci işleyicilerini ve sertifikaları ve talep Yetkilendirme Yöneticisi ve talep kimlik doğrulama Yöneticisi gibi bileşenleri yapılandırmak için kullanılacak kimlik yapılandırmasına de başvurur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-134">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="c25fa-135"><xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, öğesi, yetkilendirme kararları almak için kullanılan talep Yetkilendirme Yöneticisini ve ilkeyi yapılandıran kimlik yapılandırmasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-135">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="c25fa-136">Bu, pasif Web senaryoları olmayan senaryolarda bile geçerlidir; Örneğin, Windows Communication Foundation (WCF) uygulamaları veya Web tabanlı olmayan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="c25fa-136">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="c25fa-137">Uygulama pasif bir Web uygulaması değilse, öğesi [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) tarafından başvurulan kimlik yapılandırmasının öğesi (ve varsa alt ilke öğeleri) `<federationConfiguration>` uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-137">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="c25fa-138">Diğerlerinin hepsi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-138">All others are ignored.</span></span>  
  
 <span data-ttu-id="c25fa-139">Senaryosundan bağımsız olarak, çalışma zamanı varsayılan Federasyon yapılandırmasını yükler.</span><span class="sxs-lookup"><span data-stu-id="c25fa-139">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="c25fa-140">Davranış aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="c25fa-140">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="c25fa-141">Hiçbir `<federationConfiguration>` öğe yoksa, çalışma zamanı bir Federasyon yapılandırması oluşturur ve varsayılan değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-141">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="c25fa-142">Bu varsayılan Federasyon yapılandırması varsayılan kimlik yapılandırmasına başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-142">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="c25fa-143">Tek bir öğe varsa, bu, `<federationConfiguration>` adlandırılmış veya adlandırılmamış olmasına bakılmaksızın varsayılan Federasyon yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-143">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="c25fa-144">`identityConfiguration`Özniteliği belirtilmişse, adlandırılmış kimlik yapılandırmasına başvurulur; Aksi takdirde, varsayılan kimlik yapılandırmasına başvurulur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-144">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="c25fa-145">Adlandırılmamış bir `<federationConfiguration>` öğe varsa, varsayılan Federasyon yapılandırması olur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-145">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="c25fa-146">`identityConfiguration`Özniteliği belirtilmişse, adlandırılmış kimlik yapılandırmasına başvurulur; Aksi takdirde, varsayılan kimlik yapılandırmasına başvurulur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-146">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="c25fa-147">Birden çok adlandırılmış `<federationConfiguration>` öğe varsa ve hiçbir adlandırılmamış `<federationConfiguration>` öğe yoksa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c25fa-147">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="c25fa-148">Genellikle yalnızca tek bir `<federationConfiguration>` bölüm tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-148">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="c25fa-149">Bu bölüm varsayılan Federasyon yapılandırması ' dır.</span><span class="sxs-lookup"><span data-stu-id="c25fa-149">This section is the default federation configuration.</span></span> <span data-ttu-id="c25fa-150">Benzersiz olarak adlandırılmış birden çok `<federationConfiguration>` öğe belirtebilirsiniz; ancak, bu durumda, adlandırılmamış bir yapılandırma dışında bir Federasyon yapılandırması yüklemek istiyorsanız, için bir işleyici sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c25fa-150">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="c25fa-151"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> olay ve <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> işleyici içindeki özelliği, <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> yapılandırma dosyasındaki uygun öğeden alınan değerlerle başlatılan bir nesne olarak ayarlayın `<federationConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="c25fa-151"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="c25fa-152">`<federationConfiguration>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> .</span><span class="sxs-lookup"><span data-stu-id="c25fa-152">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="c25fa-153">Yapılandırma nesnesinin kendisi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> .</span><span class="sxs-lookup"><span data-stu-id="c25fa-153">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="c25fa-154">Özellikte tek bir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> örnek ayarlanır <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ve uygulama için Federal yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c25fa-154">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c25fa-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="c25fa-155">Example</span></span>  

 <span data-ttu-id="c25fa-156">Aşağıdaki XML, `<federationConfiguration>` WSFAB için ayarları belirten bir öğe gösterir ve varsayılan tanımlama bilgisi işleyicisinin (sınıfın bir örneği <xref:System.IdentityModel.Services.ChunkedCookieHandler> ) Sam tarafından kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c25fa-156">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c25fa-157">Bu örnekte, HTTPS kullanmak için tanımlama bilgisi işleyicisi veya WSFAE gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c25fa-157">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="c25fa-158">Bunun nedeni, `requireHttps` öğesindeki özniteliği ve içindeki `<wsFederation>` `requireSsl` özniteliğidir `<cookieHandlerElement>` `false` .</span><span class="sxs-lookup"><span data-stu-id="c25fa-158">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="c25fa-159">Bu ayarlar, çoğu üretim ortamında bir güvenlik riski sunabilecek şekilde önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c25fa-159">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"
      issuer="http://localhost:15839/wsFederationSTS/Issue"
      realm="http://localhost:50969/" reply="http://localhost:50969/"
      requireHttps="false"
      signOutReply="http://localhost:50969/SignedOutPage.html"
      signOutQueryString="Param1=value2&Param2=value2"
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c25fa-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c25fa-160">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
