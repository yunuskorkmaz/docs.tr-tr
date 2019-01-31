---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 560da96c50e99461d25c1fd65def2dc10c284470
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261678"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="c9c43-101">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="c9c43-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="c9c43-102">Belirli bir türünü belirleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9c43-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="c9c43-103">Bu özel WAS protokoller eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c43-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="c9c43-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9c43-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9c43-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="c9c43-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="c9c43-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="c9c43-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c43-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9c43-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9c43-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9c43-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c9c43-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9c43-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9c43-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9c43-110">Attributes</span></span>  
  
|<span data-ttu-id="c9c43-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9c43-111">Attribute</span></span>|<span data-ttu-id="c9c43-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9c43-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9c43-113">name</span><span class="sxs-lookup"><span data-stu-id="c9c43-113">name</span></span>|<span data-ttu-id="c9c43-114">Taşıma adı</span><span class="sxs-lookup"><span data-stu-id="c9c43-114">The name of the transport</span></span>|  
|<span data-ttu-id="c9c43-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c9c43-115">transportConfigurationType</span></span>|<span data-ttu-id="c9c43-116">Taşıma uygulayan türü</span><span class="sxs-lookup"><span data-stu-id="c9c43-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9c43-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9c43-117">Child Elements</span></span>  
  
|<span data-ttu-id="c9c43-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9c43-118">Element</span></span>|<span data-ttu-id="c9c43-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9c43-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c43-120">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="c9c43-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="c9c43-121">Belirli bir türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="c9c43-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9c43-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9c43-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c9c43-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9c43-123">Element</span></span>|<span data-ttu-id="c9c43-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9c43-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c43-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="c9c43-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="c9c43-126">Belirli bir hizmet barındırma ortamını gösteren türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9c43-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9c43-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9c43-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="c9c43-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c9c43-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
