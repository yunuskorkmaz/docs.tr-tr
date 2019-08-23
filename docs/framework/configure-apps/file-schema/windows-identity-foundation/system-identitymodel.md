---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 286ae88946692e6894ca3c7ee9e1348415c84ade
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943594"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="b7e37-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b7e37-102">\<system.identityModel></span></span>
<span data-ttu-id="b7e37-103">Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7e37-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="b7e37-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b7e37-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7e37-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7e37-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7e37-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b7e37-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7e37-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7e37-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7e37-108">Attributes</span></span>  
 <span data-ttu-id="b7e37-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="b7e37-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7e37-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7e37-110">Child Elements</span></span>  
  
|<span data-ttu-id="b7e37-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7e37-111">Element</span></span>|<span data-ttu-id="b7e37-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7e37-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e37-113">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b7e37-113">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="b7e37-114">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7e37-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7e37-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7e37-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b7e37-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7e37-116">Element</span></span>|<span data-ttu-id="b7e37-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7e37-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="b7e37-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b7e37-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7e37-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7e37-119">Remarks</span></span>  
 <span data-ttu-id="b7e37-120">Windows Identity `<system.identityModel>` Foundation (WIF) kullanmak üzere bir hizmet veya uygulamayı yapılandırmak için yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7e37-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="b7e37-121">`<system.identityModel>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.SystemIdentityModelSection> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b7e37-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7e37-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7e37-122">Example</span></span>  
 <span data-ttu-id="b7e37-123">Aşağıdaki örnek, bir yapılandırma dosyasına bir `<system.identityModel>` bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7e37-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="b7e37-124">Önce yapılandırma bölümünü ve ad alanı bildirimini `<configSections>` öğesi altına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7e37-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="b7e37-125">Daha sonra bir veya daha `<system.IdentityModel>` fazla kimlik yapılandırması belirtmek için öğesini yapılandırma dosyanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7e37-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7e37-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7e37-126">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
