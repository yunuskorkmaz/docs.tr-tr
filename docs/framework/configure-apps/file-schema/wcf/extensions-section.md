---
title: <extensions> Bölüm
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673010"
---
# <a name="extensions-section"></a><span data-ttu-id="6738e-102">\<Uzantılar > bölümü</span><span class="sxs-lookup"><span data-stu-id="6738e-102">\<extensions> section</span></span>
<span data-ttu-id="6738e-103">Bu yapılandırma bölümü, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönleri uzantıları oluşturmak kullanıcı olanak tanıyan uzantılar bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6738e-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="6738e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6738e-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6738e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6738e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6738e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6738e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6738e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6738e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6738e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6738e-108">Attributes</span></span>  
 <span data-ttu-id="6738e-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6738e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6738e-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6738e-110">Child Elements</span></span>  
  
|<span data-ttu-id="6738e-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6738e-111">Element</span></span>|<span data-ttu-id="6738e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6738e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6738e-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="6738e-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="6738e-114">Bu bölüm, hizmet veya uç nokta davranışları özelleştirmek için kullanıcı etkinleştirme davranış uzantıları, belirttiğiniz alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6738e-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="6738e-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="6738e-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="6738e-116">Bu bölümde bir makineden özel bağlama öğesinin kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="6738e-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="6738e-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="6738e-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="6738e-118">Bu bölümde, kullanıcının bağlamaları özelleştirme bağlama uzantıları, belirttiğiniz alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6738e-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="6738e-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="6738e-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="6738e-120">Bu bölümde, standart uç noktaları kaydeder alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6738e-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6738e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6738e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6738e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6738e-122">Element</span></span>|<span data-ttu-id="6738e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6738e-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6738e-124">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6738e-124">system.ServiceModel</span></span>|<span data-ttu-id="6738e-125">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6738e-125">The root element of all WCF configuration elements.</span></span>|
