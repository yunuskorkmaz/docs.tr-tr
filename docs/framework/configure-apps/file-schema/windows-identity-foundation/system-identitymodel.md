---
description: 'Daha fazla bilgi edinin: <System. IdentityModel>'
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: c597f2a849248366f9cf3847c8ef369c13d7a286
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786531"
---
# \<system.identityModel>

<span data-ttu-id="49c3c-103">Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="49c3c-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="49c3c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="49c3c-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49c3c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49c3c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="49c3c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49c3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49c3c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49c3c-107">Attributes</span></span>  

 <span data-ttu-id="49c3c-108">Yok</span><span class="sxs-lookup"><span data-stu-id="49c3c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="49c3c-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49c3c-109">Child Elements</span></span>  
  
|<span data-ttu-id="49c3c-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="49c3c-110">Element</span></span>|<span data-ttu-id="49c3c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49c3c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="49c3c-112">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49c3c-112">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49c3c-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49c3c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="49c3c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="49c3c-114">Element</span></span>|<span data-ttu-id="49c3c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49c3c-115">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="49c3c-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="49c3c-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49c3c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49c3c-117">Remarks</span></span>  

 <span data-ttu-id="49c3c-118">`<system.identityModel>`Windows Identity Foundation (WıF) kullanmak üzere bir hizmet veya uygulamayı yapılandırmak için yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="49c3c-118">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="49c3c-119">`<system.identityModel>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> .</span><span class="sxs-lookup"><span data-stu-id="49c3c-119">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49c3c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="49c3c-120">Example</span></span>  

 <span data-ttu-id="49c3c-121">Aşağıdaki örnek, `<system.identityModel>` bir yapılandırma dosyasına bir bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="49c3c-121">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="49c3c-122">Önce yapılandırma bölümünü ve ad alanı bildirimini öğesi altına eklemeniz gerekir `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="49c3c-122">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="49c3c-123">Daha sonra `<system.IdentityModel>` bir veya daha fazla kimlik yapılandırması belirtmek için öğesini yapılandırma dosyanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49c3c-123">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49c3c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49c3c-124">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
