---
title: '&lt;System.IdentityModel&gt;'
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 1b3121a6e7e036ec268cf83ffbf545c0e669a9b9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206144"
---
# <a name="ltsystemidentitymodelgt"></a><span data-ttu-id="30f48-102">&lt;System.IdentityModel&gt;</span><span class="sxs-lookup"><span data-stu-id="30f48-102">&lt;system.identityModel&gt;</span></span>
<span data-ttu-id="30f48-103">Windows Identity Foundation (WIF) seçenekleri uygulamalarda etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="30f48-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="30f48-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="30f48-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f48-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30f48-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30f48-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30f48-106">Attributes and Elements</span></span>  
 <span data-ttu-id="30f48-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30f48-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30f48-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30f48-108">Attributes</span></span>  
 <span data-ttu-id="30f48-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="30f48-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="30f48-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30f48-110">Child Elements</span></span>  
  
|<span data-ttu-id="30f48-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="30f48-111">Element</span></span>|<span data-ttu-id="30f48-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30f48-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30f48-113">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="30f48-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="30f48-114">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="30f48-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30f48-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30f48-115">Parent Elements</span></span>  
  
|<span data-ttu-id="30f48-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="30f48-116">Element</span></span>|<span data-ttu-id="30f48-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30f48-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="30f48-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="30f48-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30f48-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30f48-119">Remarks</span></span>  
 <span data-ttu-id="30f48-120">Ekleme bir `<system.identityModel>` yapılandırma dosyasına hizmet veya uygulamayı Windows Identity Foundation (WIF) kullanmak için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="30f48-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="30f48-121">`<system.identityModel>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="30f48-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f48-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="30f48-122">Example</span></span>  
 <span data-ttu-id="30f48-123">Aşağıdaki örnek nasıl ekleneceğini gösterir. bir `<system.identityModel>` bölümüne bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="30f48-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="30f48-124">Yapılandırma bölümü ve ad alanı bildirimi altında önce eklemelisiniz `<configSections>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="30f48-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="30f48-125">Ekleyebileceğiniz sonra `<system.IdentityModel>` öğesi yapılandırma dosyanıza bir veya daha fazla kimlik yapılandırmaları belirtin.</span><span class="sxs-lookup"><span data-stu-id="30f48-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30f48-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30f48-126">See Also</span></span>  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
