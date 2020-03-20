---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152510"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="fa5a4-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="fa5a4-102">\<system.identityModel.services></span></span>
<span data-ttu-id="fa5a4-103">WS-Federation protokolünü kullanarak kimlik doğrulama için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="fa5a4-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa5a4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fa5a4-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span><span class="sxs-lookup"><span data-stu-id="fa5a4-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa5a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa5a4-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa5a4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa5a4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fa5a4-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa5a4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa5a4-109">Attributes</span></span>  
 <span data-ttu-id="fa5a4-110">None</span><span class="sxs-lookup"><span data-stu-id="fa5a4-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa5a4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa5a4-111">Child Elements</span></span>  
  
|<span data-ttu-id="fa5a4-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa5a4-112">Element</span></span>|<span data-ttu-id="fa5a4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa5a4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa5a4-114">\<federasyonKonfigürasyon></span><span class="sxs-lookup"><span data-stu-id="fa5a4-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="fa5a4-115"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modüllerini yapılandıran ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa5a4-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa5a4-116">Parent Elements</span></span>  
 <span data-ttu-id="fa5a4-117">None</span><span class="sxs-lookup"><span data-stu-id="fa5a4-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa5a4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa5a4-118">Remarks</span></span>  
 <span data-ttu-id="fa5a4-119">SAM `<system.identityModel.services>` ve WSFAM ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fa5a4-120">Kodunuzda <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> talep <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> tabanlı erişim denetimi sağlamak için sınıfı veya sınıfı<xref:System.Security.Claims.ClaimsAuthorizationManager>kullanırken, talep yetkilendirme yöneticisi ( ) ve `<identityConfiguration>` yetkilendirme kararları vermek için kullanılan ilke, bu bölümdeki bir `<federationConfiguration>` öğeden örtülü veya açıkça başvurulan bir öğe aracılığıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="fa5a4-121">Daha fazla bilgi için [ \<federasyonYapılandırma>](federationconfiguration.md) öğesi altındaki **Açıklamalar'a** bakın.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="fa5a4-122">Bölüm `<system.identityModel.services>` <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sınıf tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="fa5a4-123">Bölümde yapılandırılan `<federationConfiguration>` alt öğelerin toplanması <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıf tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa5a4-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa5a4-124">Example</span></span>  
 <span data-ttu-id="fa5a4-125">Aşağıdaki XML, yapılandırma dosyasına `<system.identityModel.services>` nasıl bir bölüm ekleyeceğinigösterir.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="fa5a4-126">Öncelikle `<system.identityModel.services>` hem bölüm hem de bölümler için `<system.identityModel>` bölüm bildirimleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="fa5a4-127">(Bir `<system.identityModel.services>` bölüm eklediğinizde, gerekirse çalışma süresine `<system.identityModel>` kadar varsayılan `<identityConfiguration>` bir bölümün oluşturulabilmesini sağlamak için bölüm için bir bildirim de eklemelisiniz.) Bölüm bildirimleri eklendikten sonra, öğenin `<system.identityModel.services>` altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa5a4-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```
