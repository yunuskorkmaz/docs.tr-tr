---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941168"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="f9518-101">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="f9518-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="f9518-102">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9518-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="f9518-103">Bu, özel WAS protokolleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9518-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="f9518-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9518-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9518-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f9518-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="f9518-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="f9518-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9518-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9518-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9518-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9518-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f9518-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9518-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9518-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9518-110">Attributes</span></span>  
  
|<span data-ttu-id="f9518-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9518-111">Attribute</span></span>|<span data-ttu-id="f9518-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9518-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9518-113">name</span><span class="sxs-lookup"><span data-stu-id="f9518-113">name</span></span>|<span data-ttu-id="f9518-114">Taşımanın adı</span><span class="sxs-lookup"><span data-stu-id="f9518-114">The name of the transport</span></span>|  
|<span data-ttu-id="f9518-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="f9518-115">transportConfigurationType</span></span>|<span data-ttu-id="f9518-116">Taşımayı uygulayan tür</span><span class="sxs-lookup"><span data-stu-id="f9518-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9518-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9518-117">Child Elements</span></span>  
  
|<span data-ttu-id="f9518-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9518-118">Element</span></span>|<span data-ttu-id="f9518-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9518-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9518-120">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="f9518-120">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="f9518-121">Belirli bir taşımanın türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="f9518-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9518-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9518-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f9518-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9518-123">Element</span></span>|<span data-ttu-id="f9518-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9518-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9518-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f9518-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="f9518-126">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9518-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9518-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9518-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="f9518-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="f9518-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
