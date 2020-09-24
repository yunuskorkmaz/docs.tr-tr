---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 6545e1f1be2695d165b89a38c7218e0acdc88bfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162029"
---
# \<transportConfigurationTypes>

<span data-ttu-id="253ae-101">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="253ae-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="253ae-102">Bu, özel WAS protokolleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="253ae-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="253ae-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="253ae-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="253ae-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="253ae-104">Attributes and Elements</span></span>  

 <span data-ttu-id="253ae-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="253ae-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="253ae-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="253ae-106">Attributes</span></span>  
  
|<span data-ttu-id="253ae-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="253ae-107">Attribute</span></span>|<span data-ttu-id="253ae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="253ae-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="253ae-109">name</span><span class="sxs-lookup"><span data-stu-id="253ae-109">name</span></span>|<span data-ttu-id="253ae-110">Taşımanın adı</span><span class="sxs-lookup"><span data-stu-id="253ae-110">The name of the transport</span></span>|  
|<span data-ttu-id="253ae-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="253ae-111">transportConfigurationType</span></span>|<span data-ttu-id="253ae-112">Taşımayı uygulayan tür</span><span class="sxs-lookup"><span data-stu-id="253ae-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="253ae-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="253ae-113">Child Elements</span></span>  
  
|<span data-ttu-id="253ae-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="253ae-114">Element</span></span>|<span data-ttu-id="253ae-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="253ae-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="253ae-116">Belirli bir taşımanın türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="253ae-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="253ae-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="253ae-117">Parent Elements</span></span>  
  
|<span data-ttu-id="253ae-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="253ae-118">Element</span></span>|<span data-ttu-id="253ae-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="253ae-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="253ae-120">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="253ae-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="253ae-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="253ae-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="253ae-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="253ae-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
