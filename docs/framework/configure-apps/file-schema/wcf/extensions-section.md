---
title: "&lt;uzantılar&gt; bölümü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a564b85609ca289f382789844d4e78252bb66482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="b0d10-102">&lt;uzantılar&gt; bölümü</span><span class="sxs-lookup"><span data-stu-id="b0d10-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="b0d10-103">Bu yapılandırma bölümü kullanıcı tanımlı bağlamalar, davranışları ve diğer yönlerini uzantıları oluşturmak kullanıcı etkinleştirme uzantıları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b0d10-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="b0d10-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b0d10-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d10-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0d10-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0d10-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0d10-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b0d10-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0d10-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0d10-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0d10-108">Attributes</span></span>  
 <span data-ttu-id="b0d10-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0d10-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0d10-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0d10-110">Child Elements</span></span>  
  
|<span data-ttu-id="b0d10-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0d10-111">Element</span></span>|<span data-ttu-id="b0d10-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0d10-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0d10-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="b0d10-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="b0d10-114">Bu bölüm, hizmet veya uç nokta davranışları özelleştirmek için kullanıcı etkinleştirme davranışı uzantılarını belirtmek alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b0d10-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="b0d10-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="b0d10-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="b0d10-116">Bu bölümde özel bağlama öğesi bir makineden kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b0d10-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="b0d10-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="b0d10-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="b0d10-118">Bu bölümde bağlamaları özelleştirmek için kullanıcı etkinleştirme bağlama uzantıları belirtin alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b0d10-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="b0d10-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="b0d10-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="b0d10-120">Bu bölümde, standart uç noktaları kaydeder alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b0d10-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0d10-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0d10-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b0d10-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0d10-122">Element</span></span>|<span data-ttu-id="b0d10-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0d10-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0d10-124">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b0d10-124">system.ServiceModel</span></span>|<span data-ttu-id="b0d10-125">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="b0d10-125">The root element of all WCF configuration elements.</span></span>|
