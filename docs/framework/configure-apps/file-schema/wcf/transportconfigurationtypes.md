---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 5a51450d198ea395098f8a6a38d9104d0fe8538b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145477"
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="eb979-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="eb979-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="eb979-103">Belirli bir türünü belirleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb979-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="eb979-104">Bu özel WAS protokoller eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb979-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="eb979-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb979-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb979-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="eb979-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="eb979-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="eb979-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb979-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb979-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb979-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb979-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eb979-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb979-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb979-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eb979-111">Attributes</span></span>  
  
|<span data-ttu-id="eb979-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eb979-112">Attribute</span></span>|<span data-ttu-id="eb979-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb979-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb979-114">name</span><span class="sxs-lookup"><span data-stu-id="eb979-114">name</span></span>|<span data-ttu-id="eb979-115">Taşıma adı</span><span class="sxs-lookup"><span data-stu-id="eb979-115">The name of the transport</span></span>|  
|<span data-ttu-id="eb979-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="eb979-116">transportConfigurationType</span></span>|<span data-ttu-id="eb979-117">Taşıma uygulayan türü</span><span class="sxs-lookup"><span data-stu-id="eb979-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb979-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb979-118">Child Elements</span></span>  
  
|<span data-ttu-id="eb979-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb979-119">Element</span></span>|<span data-ttu-id="eb979-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb979-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb979-121">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="eb979-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="eb979-122">Belirli bir türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="eb979-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb979-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb979-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eb979-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb979-124">Element</span></span>|<span data-ttu-id="eb979-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb979-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb979-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="eb979-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="eb979-127">Belirli bir hizmet barındırma ortamını gösteren türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb979-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb979-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb979-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="eb979-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="eb979-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
