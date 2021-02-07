---
description: 'Daha fazla bilgi edinin: <behaviors> iş akışı'
title: <behaviors> iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 5154a389aded34065cc7bdb11d1c73d71ca9f9f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698199"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="5efac-103">\<behaviors> iş akışı</span><span class="sxs-lookup"><span data-stu-id="5efac-103">\<behaviors> of workflow</span></span>

<span data-ttu-id="5efac-104">Bu öğe **Servicedavranışlar** koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5efac-104">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="5efac-105">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5efac-105">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="5efac-106">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5efac-106">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="5efac-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5efac-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5efac-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5efac-108">Attributes and Elements</span></span>  

 <span data-ttu-id="5efac-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5efac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5efac-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5efac-110">Attributes</span></span>  

 <span data-ttu-id="5efac-111">Yok</span><span class="sxs-lookup"><span data-stu-id="5efac-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5efac-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5efac-112">Child Elements</span></span>  
  
|<span data-ttu-id="5efac-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5efac-113">Element</span></span>|<span data-ttu-id="5efac-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5efac-114">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="5efac-115">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5efac-115">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5efac-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5efac-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5efac-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5efac-117">Element</span></span>|<span data-ttu-id="5efac-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5efac-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="5efac-119">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5efac-119">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5efac-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5efac-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="5efac-121">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="5efac-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
