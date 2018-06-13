---
title: '&lt;uzantılar&gt; bölümü'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 09cabfc6c03602c3b6de343a29b5b25755f2cf0f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750144"
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="e8b63-102">&lt;uzantılar&gt; bölümü</span><span class="sxs-lookup"><span data-stu-id="e8b63-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="e8b63-103">Bu yapılandırma bölümü kullanıcı tanımlı bağlamalar, davranışları ve diğer yönlerini uzantıları oluşturmak kullanıcı etkinleştirme uzantıları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e8b63-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="e8b63-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e8b63-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b63-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8b63-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8b63-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8b63-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e8b63-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8b63-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8b63-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8b63-108">Attributes</span></span>  
 <span data-ttu-id="e8b63-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8b63-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8b63-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8b63-110">Child Elements</span></span>  
  
|<span data-ttu-id="e8b63-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8b63-111">Element</span></span>|<span data-ttu-id="e8b63-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8b63-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8b63-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8b63-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="e8b63-114">Bu bölüm, hizmet veya uç nokta davranışları özelleştirmek için kullanıcı etkinleştirme davranışı uzantılarını belirtmek alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e8b63-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="e8b63-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8b63-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="e8b63-116">Bu bölümde özel bağlama öğesi bir makineden kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="e8b63-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="e8b63-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8b63-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="e8b63-118">Bu bölümde bağlamaları özelleştirmek için kullanıcı etkinleştirme bağlama uzantıları belirtin alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e8b63-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="e8b63-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8b63-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="e8b63-120">Bu bölümde, standart uç noktaları kaydeder alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e8b63-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8b63-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8b63-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e8b63-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8b63-122">Element</span></span>|<span data-ttu-id="e8b63-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8b63-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8b63-124">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e8b63-124">system.ServiceModel</span></span>|<span data-ttu-id="e8b63-125">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8b63-125">The root element of all WCF configuration elements.</span></span>|
