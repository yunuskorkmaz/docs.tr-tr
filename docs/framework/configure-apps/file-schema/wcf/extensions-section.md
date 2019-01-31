---
title: <extensions> Bölüm
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268294"
---
# <a name="extensions-section"></a><span data-ttu-id="4f7f2-102">\<Uzantılar > bölümü</span><span class="sxs-lookup"><span data-stu-id="4f7f2-102">\<extensions> section</span></span>
<span data-ttu-id="4f7f2-103">Bu yapılandırma bölümü, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönleri uzantıları oluşturmak kullanıcı olanak tanıyan uzantılar bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="4f7f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4f7f2-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f7f2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f7f2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f7f2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4f7f2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f7f2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f7f2-108">Attributes</span></span>  
 <span data-ttu-id="4f7f2-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f7f2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f7f2-110">Child Elements</span></span>  
  
|<span data-ttu-id="4f7f2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f7f2-111">Element</span></span>|<span data-ttu-id="4f7f2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f7f2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f7f2-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="4f7f2-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="4f7f2-114">Bu bölüm, hizmet veya uç nokta davranışları özelleştirmek için kullanıcı etkinleştirme davranış uzantıları, belirttiğiniz alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="4f7f2-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="4f7f2-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="4f7f2-116">Bu bölümde bir makineden özel bağlama öğesinin kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="4f7f2-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="4f7f2-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="4f7f2-118">Bu bölümde, kullanıcının bağlamaları özelleştirme bağlama uzantıları, belirttiğiniz alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="4f7f2-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="4f7f2-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="4f7f2-120">Bu bölümde, standart uç noktaları kaydeder alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f7f2-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f7f2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4f7f2-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f7f2-122">Element</span></span>|<span data-ttu-id="4f7f2-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f7f2-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f7f2-124">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4f7f2-124">system.ServiceModel</span></span>|<span data-ttu-id="4f7f2-125">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4f7f2-125">The root element of all WCF configuration elements.</span></span>|
