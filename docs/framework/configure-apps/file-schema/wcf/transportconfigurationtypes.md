---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a4f9396537446920b8976d1bd076fcd5ce5876c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="c7580-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="c7580-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="c7580-103">Belirli bir tür belirleme yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c7580-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="c7580-104">Bu özel WAS protokoller eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7580-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="c7580-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c7580-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c7580-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="c7580-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="c7580-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="c7580-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7580-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7580-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7580-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7580-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c7580-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7580-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7580-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7580-111">Attributes</span></span>  
  
|<span data-ttu-id="c7580-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7580-112">Attribute</span></span>|<span data-ttu-id="c7580-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7580-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7580-114">name</span><span class="sxs-lookup"><span data-stu-id="c7580-114">name</span></span>|<span data-ttu-id="c7580-115">Taşıma adı</span><span class="sxs-lookup"><span data-stu-id="c7580-115">The name of the transport</span></span>|  
|<span data-ttu-id="c7580-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c7580-116">transportConfigurationType</span></span>|<span data-ttu-id="c7580-117">Taşıma uygulayan türü</span><span class="sxs-lookup"><span data-stu-id="c7580-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7580-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7580-118">Child Elements</span></span>  
  
|<span data-ttu-id="c7580-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7580-119">Element</span></span>|<span data-ttu-id="c7580-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7580-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7580-121">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c7580-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="c7580-122">Belirli bir aktarım türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="c7580-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7580-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7580-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c7580-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7580-124">Element</span></span>|<span data-ttu-id="c7580-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7580-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7580-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="c7580-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="c7580-127">Belirli bir barındırma ortamı hizmeti başlatır türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7580-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7580-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7580-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="c7580-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c7580-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
