---
title: <extensions>kısmı
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 4c8b5fe6eef1863ee3f02cb761a3aac61406e446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918964"
---
# <a name="extensions-section"></a><span data-ttu-id="68b4e-102">\<uzantılar > bölümü</span><span class="sxs-lookup"><span data-stu-id="68b4e-102">\<extensions> section</span></span>
<span data-ttu-id="68b4e-103">Bu yapılandırma bölümü, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantıların diğer yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="68b4e-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="68b4e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68b4e-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b4e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68b4e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68b4e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b4e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="68b4e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68b4e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68b4e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68b4e-108">Attributes</span></span>  
 <span data-ttu-id="68b4e-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="68b4e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68b4e-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b4e-110">Child Elements</span></span>  
  
|<span data-ttu-id="68b4e-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="68b4e-111">Element</span></span>|<span data-ttu-id="68b4e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b4e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68b4e-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="68b4e-113">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="68b4e-114">Bu bölüm, kullanıcının hizmet veya uç nokta davranışlarını özelleştirmesini sağlayan davranış uzantılarını belirten alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="68b4e-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="68b4e-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="68b4e-115">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="68b4e-116">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="68b4e-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="68b4e-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="68b4e-117">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="68b4e-118">Bu bölüm, bağlama uzantıları belirten, kullanıcının bağlamaları özelleştirmesini sağlayan alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="68b4e-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="68b4e-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="68b4e-119">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="68b4e-120">Bu bölüm, standart uç noktaları kaydeden alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="68b4e-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68b4e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b4e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="68b4e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="68b4e-122">Element</span></span>|<span data-ttu-id="68b4e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b4e-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68b4e-124">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="68b4e-124">system.ServiceModel</span></span>|<span data-ttu-id="68b4e-125">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="68b4e-125">The root element of all WCF configuration elements.</span></span>|
