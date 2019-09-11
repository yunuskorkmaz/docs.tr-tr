---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854932"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="60aeb-101">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="60aeb-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="60aeb-102">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="60aeb-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="60aeb-103">Bu, özel WAS protokolleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60aeb-103">This can be used to add custom WAS protocols.</span></span>  
  
<span data-ttu-id="60aeb-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60aeb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60aeb-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="60aeb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="60aeb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="60aeb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="60aeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transportConfigurationTypes >**</span><span class="sxs-lookup"><span data-stu-id="60aeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60aeb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60aeb-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60aeb-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60aeb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="60aeb-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60aeb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60aeb-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60aeb-111">Attributes</span></span>  
  
|<span data-ttu-id="60aeb-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60aeb-112">Attribute</span></span>|<span data-ttu-id="60aeb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60aeb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60aeb-114">name</span><span class="sxs-lookup"><span data-stu-id="60aeb-114">name</span></span>|<span data-ttu-id="60aeb-115">Taşımanın adı</span><span class="sxs-lookup"><span data-stu-id="60aeb-115">The name of the transport</span></span>|  
|<span data-ttu-id="60aeb-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="60aeb-116">transportConfigurationType</span></span>|<span data-ttu-id="60aeb-117">Taşımayı uygulayan tür</span><span class="sxs-lookup"><span data-stu-id="60aeb-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60aeb-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60aeb-118">Child Elements</span></span>  
  
|<span data-ttu-id="60aeb-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="60aeb-119">Element</span></span>|<span data-ttu-id="60aeb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60aeb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60aeb-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="60aeb-121">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="60aeb-122">Belirli bir taşımanın türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="60aeb-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60aeb-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60aeb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="60aeb-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="60aeb-124">Element</span></span>|<span data-ttu-id="60aeb-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60aeb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60aeb-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="60aeb-126">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="60aeb-127">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60aeb-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60aeb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60aeb-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="60aeb-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="60aeb-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
