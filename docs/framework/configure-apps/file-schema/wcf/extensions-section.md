---
description: 'Hakkında daha fazla bilgi edinin: <extensions> bölüm'
title: <extensions> kısmı
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 65b1de76155b1e3fbd8e5f14a5f4a1cb8c180ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664697"
---
# <a name="extensions-section"></a><span data-ttu-id="ceda7-103">\<extensions> kısmı</span><span class="sxs-lookup"><span data-stu-id="ceda7-103">\<extensions> section</span></span>

<span data-ttu-id="ceda7-104">Bu yapılandırma bölümü, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantıların diğer yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="ceda7-104">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="ceda7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ceda7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceda7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceda7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ceda7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ceda7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceda7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ceda7-108">Attributes</span></span>  

 <span data-ttu-id="ceda7-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="ceda7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ceda7-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceda7-110">Child Elements</span></span>  
  
|<span data-ttu-id="ceda7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceda7-111">Element</span></span>|<span data-ttu-id="ceda7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceda7-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="ceda7-113">Bu bölüm, kullanıcının hizmet veya uç nokta davranışlarını özelleştirmesini sağlayan davranış uzantılarını belirten alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ceda7-113">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="ceda7-114">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="ceda7-114">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="ceda7-115">Bu bölüm, bağlama uzantıları belirten, kullanıcının bağlamaları özelleştirmesini sağlayan alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ceda7-115">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="ceda7-116">Bu bölüm, standart uç noktaları kaydeden alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ceda7-116">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceda7-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceda7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ceda7-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceda7-118">Element</span></span>|<span data-ttu-id="ceda7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceda7-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ceda7-120">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ceda7-120">system.ServiceModel</span></span>|<span data-ttu-id="ceda7-121">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="ceda7-121">The root element of all WCF configuration elements.</span></span>|
