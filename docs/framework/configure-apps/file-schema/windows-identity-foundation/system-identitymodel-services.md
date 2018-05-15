---
title: '&lt;system.identityModel.services&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca108d7dd0498b0d7c08bb632ab45c7229ff58c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemidentitymodelservicesgt"></a><span data-ttu-id="4a91b-102">&lt;system.identityModel.services&gt;</span><span class="sxs-lookup"><span data-stu-id="4a91b-102">&lt;system.identityModel.services&gt;</span></span>
<span data-ttu-id="4a91b-103">WS-Federasyon protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="4a91b-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="4a91b-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="4a91b-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a91b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a91b-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a91b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a91b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4a91b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a91b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a91b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a91b-108">Attributes</span></span>  
 <span data-ttu-id="4a91b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a91b-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a91b-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a91b-110">Child Elements</span></span>  
  
|<span data-ttu-id="4a91b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a91b-111">Element</span></span>|<span data-ttu-id="4a91b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a91b-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a91b-113">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="4a91b-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="4a91b-114">Yapılandırma ayarlarını içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modülleri.</span><span class="sxs-lookup"><span data-stu-id="4a91b-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a91b-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a91b-115">Parent Elements</span></span>  
 <span data-ttu-id="4a91b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a91b-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a91b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a91b-117">Remarks</span></span>  
 <span data-ttu-id="4a91b-118">Ekleme bir `<system.identityModel.services>` SAM ve WSFAM için ayarları sağlamak için uygulamanızın yapılandırma dosyasına bölümü.</span><span class="sxs-lookup"><span data-stu-id="4a91b-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a91b-119">Kullanırken <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> veya <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> talep Yetkilendirme Yöneticisi'ni kodunuzda talep tabanlı erişim denetimi sağlamak için sınıfı (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ve yetkilendirme kararları vermek için kullanılan ilke aracılığıyla yapılandırılmış olan bir `<identityConfiguration>` içinden örtük veya açık olarak başvuruda öğesi bir `<federationConfiguration>` bu bölümdeki öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a91b-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="4a91b-120">Daha fazla bilgi için bkz: **açıklamalar** altında [ \<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a91b-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="4a91b-121">`<system.identityModel.services>` Bölümünde belirtildiği <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4a91b-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="4a91b-122">Alt koleksiyonunu `<federationConfiguration>` bölümünde yapılandırılmış öğeleri ile temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4a91b-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a91b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a91b-123">Example</span></span>  
 <span data-ttu-id="4a91b-124">Aşağıdaki XML nasıl ekleneceğini gösterir bir `<system.identityModel.services>` bölümüne bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4a91b-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="4a91b-125">İlk bölüm bildirimlerin her ikisi için de eklemelisiniz `<system.identityModel.services>` bölüm ve `<system.identityModel>` bölümler.</span><span class="sxs-lookup"><span data-stu-id="4a91b-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="4a91b-126">(Eklediğinizde bir `<system.identityModel.services>` bölüm için bir bildirim de eklemeniz `<system.identityModel>` varsayılan emin olmak için bölüm `<identityConfiguration>` bölüm gerekirse çalışma zamanı tarafından oluşturulabilir.) Bölüm bildirimlerin ekledikten sonra Federasyon kimlik doğrulaması ayarlar altında yapılandırabilirsiniz `<system.identityModel.services>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a91b-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
