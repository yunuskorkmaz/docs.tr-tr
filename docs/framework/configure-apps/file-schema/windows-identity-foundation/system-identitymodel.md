---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251799"
---
# \<system.identityModel>
<span data-ttu-id="19903-102">Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="19903-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="19903-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19903-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19903-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19903-104">Attributes and Elements</span></span>  
 <span data-ttu-id="19903-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19903-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19903-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19903-106">Attributes</span></span>  
 <span data-ttu-id="19903-107">Yok</span><span class="sxs-lookup"><span data-stu-id="19903-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19903-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19903-108">Child Elements</span></span>  
  
|<span data-ttu-id="19903-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="19903-109">Element</span></span>|<span data-ttu-id="19903-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19903-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="19903-111">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19903-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19903-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19903-112">Parent Elements</span></span>  
  
|<span data-ttu-id="19903-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="19903-113">Element</span></span>|<span data-ttu-id="19903-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19903-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="19903-115">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="19903-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19903-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19903-116">Remarks</span></span>  
 <span data-ttu-id="19903-117">`<system.identityModel>`Windows Identity Foundation (WıF) kullanmak üzere bir hizmet veya uygulamayı yapılandırmak için yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19903-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="19903-118">`<system.identityModel>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> .</span><span class="sxs-lookup"><span data-stu-id="19903-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19903-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="19903-119">Example</span></span>  
 <span data-ttu-id="19903-120">Aşağıdaki örnek, `<system.identityModel>` bir yapılandırma dosyasına bir bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19903-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="19903-121">Önce yapılandırma bölümünü ve ad alanı bildirimini öğesi altına eklemeniz gerekir `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="19903-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="19903-122">Daha sonra `<system.IdentityModel>` bir veya daha fazla kimlik yapılandırması belirtmek için öğesini yapılandırma dosyanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19903-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19903-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19903-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
