---
title: <extensions>kısmı
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855363"
---
# <a name="extensions-section"></a><span data-ttu-id="3a01e-102">\<uzantılar > bölümü</span><span class="sxs-lookup"><span data-stu-id="3a01e-102">\<extensions> section</span></span>
<span data-ttu-id="3a01e-103">Bu yapılandırma bölümü, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantıların diğer yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="3a01e-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="3a01e-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a01e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a01e-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3a01e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3a01e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<uzantılar >**</span><span class="sxs-lookup"><span data-stu-id="3a01e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a01e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a01e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a01e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a01e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3a01e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a01e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a01e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a01e-110">Attributes</span></span>  
 <span data-ttu-id="3a01e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a01e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a01e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a01e-112">Child Elements</span></span>  
  
|<span data-ttu-id="3a01e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a01e-113">Element</span></span>|<span data-ttu-id="3a01e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a01e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a01e-115">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="3a01e-115">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="3a01e-116">Bu bölüm, kullanıcının hizmet veya uç nokta davranışlarını özelleştirmesini sağlayan davranış uzantılarını belirten alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a01e-116">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="3a01e-117">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="3a01e-117">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="3a01e-118">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="3a01e-118">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="3a01e-119">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="3a01e-119">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="3a01e-120">Bu bölüm, bağlama uzantıları belirten, kullanıcının bağlamaları özelleştirmesini sağlayan alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a01e-120">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="3a01e-121">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="3a01e-121">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="3a01e-122">Bu bölüm, standart uç noktaları kaydeden alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a01e-122">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a01e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a01e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3a01e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a01e-124">Element</span></span>|<span data-ttu-id="3a01e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a01e-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a01e-126">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3a01e-126">system.ServiceModel</span></span>|<span data-ttu-id="3a01e-127">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="3a01e-127">The root element of all WCF configuration elements.</span></span>|
