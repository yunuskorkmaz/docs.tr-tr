---
description: 'Hakkında daha fazla bilgi edinin: <transportConfigurationTypes>'
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: d6ef92cf3bdd10fdc9b374f10aaa748cf4300529
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749278"
---
# \<transportConfigurationTypes>

<span data-ttu-id="bebf2-102">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bebf2-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="bebf2-103">Bu, özel WAS protokolleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bebf2-103">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="bebf2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bebf2-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bebf2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bebf2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bebf2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bebf2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bebf2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bebf2-107">Attributes</span></span>  
  
|<span data-ttu-id="bebf2-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bebf2-108">Attribute</span></span>|<span data-ttu-id="bebf2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bebf2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bebf2-110">name</span><span class="sxs-lookup"><span data-stu-id="bebf2-110">name</span></span>|<span data-ttu-id="bebf2-111">Taşımanın adı</span><span class="sxs-lookup"><span data-stu-id="bebf2-111">The name of the transport</span></span>|  
|<span data-ttu-id="bebf2-112">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="bebf2-112">transportConfigurationType</span></span>|<span data-ttu-id="bebf2-113">Taşımayı uygulayan tür</span><span class="sxs-lookup"><span data-stu-id="bebf2-113">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bebf2-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bebf2-114">Child Elements</span></span>  
  
|<span data-ttu-id="bebf2-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="bebf2-115">Element</span></span>|<span data-ttu-id="bebf2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bebf2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="bebf2-117">Belirli bir taşımanın türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="bebf2-117">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bebf2-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bebf2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bebf2-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="bebf2-119">Element</span></span>|<span data-ttu-id="bebf2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bebf2-120">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="bebf2-121">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bebf2-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bebf2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bebf2-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="bebf2-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="bebf2-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
