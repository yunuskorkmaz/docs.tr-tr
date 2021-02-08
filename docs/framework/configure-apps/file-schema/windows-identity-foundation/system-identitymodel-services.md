---
description: 'Hakkında daha fazla bilgi edinin: <System. IdentityModel. Services>'
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 037a96c2620e06ef6aed85d1dbaba62aca72e9eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786557"
---
# \<system.identityModel.services>

<span data-ttu-id="95779-103">WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="95779-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="95779-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="95779-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95779-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95779-105">Attributes and Elements</span></span>  

 <span data-ttu-id="95779-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95779-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95779-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95779-107">Attributes</span></span>  

 <span data-ttu-id="95779-108">Yok</span><span class="sxs-lookup"><span data-stu-id="95779-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95779-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95779-109">Child Elements</span></span>  
  
|<span data-ttu-id="95779-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="95779-110">Element</span></span>|<span data-ttu-id="95779-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95779-111">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="95779-112"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) http modüllerini yapılandıran ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="95779-112">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95779-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95779-113">Parent Elements</span></span>  

 <span data-ttu-id="95779-114">Yok</span><span class="sxs-lookup"><span data-stu-id="95779-114">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95779-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95779-115">Remarks</span></span>  

 <span data-ttu-id="95779-116">`<system.identityModel.services>`Sam ve WSFAE ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95779-116">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="95779-117"><xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, <xref:System.Security.Claims.ClaimsAuthorizationManager> yetkilendirme kararları vermek için kullanılan talep Yetkilendirme Yöneticisi () ve ilke, `<identityConfiguration>` Bu bölümdeki bir öğeden örtük olarak veya açıkça başvurulan bir öğe aracılığıyla yapılandırılır `<federationConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="95779-117">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="95779-118">Daha fazla bilgi için, öğesinin **altındaki açıklamalara** bakın [\<federationConfiguration>](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="95779-118">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="95779-119">`<system.identityModel.services>`Bölümü sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> .</span><span class="sxs-lookup"><span data-stu-id="95779-119">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="95779-120">`<federationConfiguration>`Bölümünde yapılandırılan alt öğelerin koleksiyonu sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> .</span><span class="sxs-lookup"><span data-stu-id="95779-120">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95779-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="95779-121">Example</span></span>  

 <span data-ttu-id="95779-122">Aşağıdaki XML, `<system.identityModel.services>` bir yapılandırma dosyasına bir bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="95779-122">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="95779-123">Öncelikle bölüm ve bölümler için bölüm bildirimleri eklemeniz gerekir `<system.identityModel.services>` `<system.identityModel>` .</span><span class="sxs-lookup"><span data-stu-id="95779-123">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="95779-124">(Bir `<system.identityModel.services>` bölümü eklediğinizde, `<system.identityModel>` `<identityConfiguration>` gerekirse çalışma zamanı tarafından varsayılan bir bölümün oluşturulabilmelidir emin olmak için bölüm için bir bildirim de eklemeniz gerekir.) Bölüm bildirimleri eklendikten sonra, öğesinin altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz `<system.identityModel.services>` .</span><span class="sxs-lookup"><span data-stu-id="95779-124">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
