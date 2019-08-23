---
title: <behaviors>iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946002"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="9695c-102">\<iş akışının davranışlar ></span><span class="sxs-lookup"><span data-stu-id="9695c-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="9695c-103">Bu öğe **Servicedavranışlar** koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9695c-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="9695c-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9695c-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="9695c-105">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9695c-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="9695c-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9695c-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9695c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9695c-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9695c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9695c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9695c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9695c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9695c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9695c-110">Attributes</span></span>  
 <span data-ttu-id="9695c-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="9695c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9695c-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9695c-112">Child Elements</span></span>  
  
|<span data-ttu-id="9695c-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="9695c-113">Element</span></span>|<span data-ttu-id="9695c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9695c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9695c-115">\<Servicedavranışlar ></span><span class="sxs-lookup"><span data-stu-id="9695c-115">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="9695c-116">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9695c-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9695c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9695c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9695c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="9695c-118">Element</span></span>|<span data-ttu-id="9695c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9695c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9695c-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9695c-120">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="9695c-121">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9695c-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9695c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9695c-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="9695c-123">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="9695c-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
