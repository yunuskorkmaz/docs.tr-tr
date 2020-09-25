---
title: <extensions> kısmı
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: f3eb5d446291dfa6b7c8e0f1ee2b6a5cf53c2162
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185788"
---
# <a name="extensions-section"></a><span data-ttu-id="a272e-102">\<extensions> kısmı</span><span class="sxs-lookup"><span data-stu-id="a272e-102">\<extensions> section</span></span>

<span data-ttu-id="a272e-103">Bu yapılandırma bölümü, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantıların diğer yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="a272e-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="a272e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a272e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a272e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a272e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a272e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a272e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a272e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a272e-107">Attributes</span></span>  

 <span data-ttu-id="a272e-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="a272e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a272e-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a272e-109">Child Elements</span></span>  
  
|<span data-ttu-id="a272e-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="a272e-110">Element</span></span>|<span data-ttu-id="a272e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a272e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="a272e-112">Bu bölüm, kullanıcının hizmet veya uç nokta davranışlarını özelleştirmesini sağlayan davranış uzantılarını belirten alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a272e-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="a272e-113">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="a272e-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="a272e-114">Bu bölüm, bağlama uzantıları belirten, kullanıcının bağlamaları özelleştirmesini sağlayan alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a272e-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="a272e-115">Bu bölüm, standart uç noktaları kaydeden alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a272e-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a272e-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a272e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a272e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a272e-117">Element</span></span>|<span data-ttu-id="a272e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a272e-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a272e-119">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a272e-119">system.ServiceModel</span></span>|<span data-ttu-id="a272e-120">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a272e-120">The root element of all WCF configuration elements.</span></span>|
