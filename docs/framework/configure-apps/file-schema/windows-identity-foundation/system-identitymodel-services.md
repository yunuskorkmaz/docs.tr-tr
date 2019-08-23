---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943653"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="c316b-102">\<System. IdentityModel. Services ></span><span class="sxs-lookup"><span data-stu-id="c316b-102">\<system.identityModel.services></span></span>
<span data-ttu-id="c316b-103">WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="c316b-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="c316b-104">\<System. IdentityModel. Services ></span><span class="sxs-lookup"><span data-stu-id="c316b-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c316b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c316b-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c316b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c316b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c316b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c316b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c316b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c316b-108">Attributes</span></span>  
 <span data-ttu-id="c316b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c316b-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c316b-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c316b-110">Child Elements</span></span>  
  
|<span data-ttu-id="c316b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="c316b-111">Element</span></span>|<span data-ttu-id="c316b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c316b-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c316b-113">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c316b-113">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="c316b-114"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfab) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) http modüllerini yapılandıran ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="c316b-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c316b-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c316b-115">Parent Elements</span></span>  
 <span data-ttu-id="c316b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c316b-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c316b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c316b-117">Remarks</span></span>  
 <span data-ttu-id="c316b-118">Sam ve `<system.identityModel.services>` wsfae ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c316b-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c316b-119">Kodunuzda talep tabanlı <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> erişim denetimi <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> sağlamak için veya sınıfını kullanırken, yetkilendirme kararları almak için kullanılan talep Yetkilendirme Yöneticisi (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ve ilkesi bir `<identityConfiguration>` Bu bölümdeki bir `<federationConfiguration>` öğeden örtük veya açık olarak başvurulan öğe.</span><span class="sxs-lookup"><span data-stu-id="c316b-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="c316b-120">Daha fazla bilgi için [ \<FederationConfiguration >](federationconfiguration.md) öğesinin altındaki açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="c316b-120">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="c316b-121">`<system.identityModel.services>` Bölümü sınıfı<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c316b-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="c316b-122">Bölümünde yapılandırılan alt `<federationConfiguration>` öğelerin koleksiyonu <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c316b-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c316b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="c316b-123">Example</span></span>  
 <span data-ttu-id="c316b-124">Aşağıdaki XML, bir yapılandırma dosyasına bir `<system.identityModel.services>` bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c316b-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="c316b-125">Öncelikle `<system.identityModel.services>` bölüm`<system.identityModel>` ve bölümler için bölüm bildirimleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c316b-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="c316b-126">(Bir `<system.identityModel.services>` bölümü eklediğinizde, gerekirse çalışma zamanı tarafından varsayılan `<identityConfiguration>` bir bölümün oluşturulabilmelidir emin `<system.identityModel>` olmak için bölüm için bir bildirim de eklemeniz gerekir.) Bölüm bildirimleri eklendikten sonra, `<system.identityModel.services>` öğesinin altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c316b-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
