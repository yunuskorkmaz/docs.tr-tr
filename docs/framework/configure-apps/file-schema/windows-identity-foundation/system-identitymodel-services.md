---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e909756a58d5008d917fca84af0e478fc4878d2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156816"
---
# \<system.identityModel.services>

<span data-ttu-id="d1cc3-102">WS-Federation protokolünü kullanarak kimlik doğrulaması için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="d1cc3-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="d1cc3-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1cc3-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1cc3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1cc3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d1cc3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1cc3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1cc3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1cc3-106">Attributes</span></span>  

 <span data-ttu-id="d1cc3-107">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="d1cc3-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1cc3-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1cc3-108">Child Elements</span></span>  
  
|<span data-ttu-id="d1cc3-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1cc3-109">Element</span></span>|<span data-ttu-id="d1cc3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1cc3-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="d1cc3-111"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) http modüllerini yapılandıran ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d1cc3-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1cc3-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1cc3-112">Parent Elements</span></span>  

 <span data-ttu-id="d1cc3-113">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="d1cc3-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1cc3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1cc3-114">Remarks</span></span>  

 <span data-ttu-id="d1cc3-115">`<system.identityModel.services>`Sam ve WSFAE ayarlarını sağlamak için uygulamanızın yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1cc3-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1cc3-116"><xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> Kodunuzda talep tabanlı erişim denetimi sağlamak için veya sınıfını kullanırken, <xref:System.Security.Claims.ClaimsAuthorizationManager> yetkilendirme kararları vermek için kullanılan talep Yetkilendirme Yöneticisi () ve ilke, `<identityConfiguration>` Bu bölümdeki bir öğeden örtük olarak veya açıkça başvurulan bir öğe aracılığıyla yapılandırılır `<federationConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="d1cc3-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="d1cc3-117">Daha fazla bilgi için, öğesinin **altındaki açıklamalara** bakın [\<federationConfiguration>](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="d1cc3-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="d1cc3-118">`<system.identityModel.services>`Bölümü sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> .</span><span class="sxs-lookup"><span data-stu-id="d1cc3-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="d1cc3-119">`<federationConfiguration>`Bölümünde yapılandırılan alt öğelerin koleksiyonu sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> .</span><span class="sxs-lookup"><span data-stu-id="d1cc3-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1cc3-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1cc3-120">Example</span></span>  

 <span data-ttu-id="d1cc3-121">Aşağıdaki XML, `<system.identityModel.services>` bir yapılandırma dosyasına bir bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1cc3-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="d1cc3-122">Öncelikle bölüm ve bölümler için bölüm bildirimleri eklemeniz gerekir `<system.identityModel.services>` `<system.identityModel>` .</span><span class="sxs-lookup"><span data-stu-id="d1cc3-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="d1cc3-123">(Bir `<system.identityModel.services>` bölümü eklediğinizde, `<system.identityModel>` `<identityConfiguration>` gerekirse çalışma zamanı tarafından varsayılan bir bölümün oluşturulabilmelidir emin olmak için bölüm için bir bildirim de eklemeniz gerekir.) Bölüm bildirimleri eklendikten sonra, öğesinin altında federal kimlik doğrulama ayarlarını yapılandırabilirsiniz `<system.identityModel.services>` .</span><span class="sxs-lookup"><span data-stu-id="d1cc3-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
