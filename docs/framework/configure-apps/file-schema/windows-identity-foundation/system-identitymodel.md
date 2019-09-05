---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251799"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="21eab-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="21eab-102">\<system.identityModel></span></span>
<span data-ttu-id="21eab-103">Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="21eab-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
<span data-ttu-id="21eab-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="21eab-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="21eab-105">&nbsp;&nbsp; **\<System. IdentityModel >**</span><span class="sxs-lookup"><span data-stu-id="21eab-105">&nbsp;&nbsp;**\<system.identityModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21eab-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21eab-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21eab-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21eab-107">Attributes and Elements</span></span>  
 <span data-ttu-id="21eab-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21eab-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21eab-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21eab-109">Attributes</span></span>  
 <span data-ttu-id="21eab-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="21eab-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21eab-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21eab-111">Child Elements</span></span>  
  
|<span data-ttu-id="21eab-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="21eab-112">Element</span></span>|<span data-ttu-id="21eab-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21eab-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21eab-114">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="21eab-114">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="21eab-115">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21eab-115">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21eab-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21eab-116">Parent Elements</span></span>  
  
|<span data-ttu-id="21eab-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="21eab-117">Element</span></span>|<span data-ttu-id="21eab-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21eab-118">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="21eab-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="21eab-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21eab-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21eab-120">Remarks</span></span>  
 <span data-ttu-id="21eab-121">Windows Identity `<system.identityModel>` Foundation (WIF) kullanmak üzere bir hizmet veya uygulamayı yapılandırmak için yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="21eab-121">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="21eab-122">`<system.identityModel>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.SystemIdentityModelSection> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="21eab-122">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21eab-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="21eab-123">Example</span></span>  
 <span data-ttu-id="21eab-124">Aşağıdaki örnek, bir yapılandırma dosyasına bir `<system.identityModel>` bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21eab-124">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="21eab-125">Önce yapılandırma bölümünü ve ad alanı bildirimini `<configSections>` öğesi altına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21eab-125">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="21eab-126">Daha sonra bir veya daha `<system.IdentityModel>` fazla kimlik yapılandırması belirtmek için öğesini yapılandırma dosyanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21eab-126">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21eab-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21eab-127">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
