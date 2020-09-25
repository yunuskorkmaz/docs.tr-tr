---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 216b4c73e06469d6577c61338ad1af0fdd2dc05e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185580"
---
# \<system.identityModel>

<span data-ttu-id="faeee-102">Uygulamalarda Windows Identity Foundation (WıF) seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="faeee-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="faeee-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="faeee-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faeee-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="faeee-104">Attributes and Elements</span></span>  

 <span data-ttu-id="faeee-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="faeee-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faeee-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="faeee-106">Attributes</span></span>  

 <span data-ttu-id="faeee-107">Yok</span><span class="sxs-lookup"><span data-stu-id="faeee-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="faeee-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="faeee-108">Child Elements</span></span>  
  
|<span data-ttu-id="faeee-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="faeee-109">Element</span></span>|<span data-ttu-id="faeee-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faeee-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="faeee-111">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="faeee-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="faeee-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="faeee-112">Parent Elements</span></span>  
  
|<span data-ttu-id="faeee-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="faeee-113">Element</span></span>|<span data-ttu-id="faeee-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faeee-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="faeee-115">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="faeee-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faeee-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faeee-116">Remarks</span></span>  

 <span data-ttu-id="faeee-117">`<system.identityModel>`Windows Identity Foundation (WıF) kullanmak üzere bir hizmet veya uygulamayı yapılandırmak için yapılandırma dosyasına bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="faeee-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="faeee-118">`<system.identityModel>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> .</span><span class="sxs-lookup"><span data-stu-id="faeee-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faeee-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="faeee-119">Example</span></span>  

 <span data-ttu-id="faeee-120">Aşağıdaki örnek, `<system.identityModel>` bir yapılandırma dosyasına bir bölümün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="faeee-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="faeee-121">Önce yapılandırma bölümünü ve ad alanı bildirimini öğesi altına eklemeniz gerekir `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="faeee-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="faeee-122">Daha sonra `<system.IdentityModel>` bir veya daha fazla kimlik yapılandırması belirtmek için öğesini yapılandırma dosyanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="faeee-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faeee-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faeee-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
