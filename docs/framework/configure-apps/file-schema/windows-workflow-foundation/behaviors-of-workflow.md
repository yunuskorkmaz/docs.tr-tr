---
title: <behaviors>iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398872"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="809be-102">\<iş akışının davranışlar ></span><span class="sxs-lookup"><span data-stu-id="809be-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="809be-103">Bu öğe **Servicedavranışlar** koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="809be-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="809be-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="809be-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="809be-105">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="809be-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
<span data-ttu-id="809be-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="809be-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="809be-107">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="809be-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="809be-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<davranışlar >**</span><span class="sxs-lookup"><span data-stu-id="809be-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="809be-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="809be-109">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="809be-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="809be-110">Attributes and Elements</span></span>  
 <span data-ttu-id="809be-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="809be-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="809be-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="809be-112">Attributes</span></span>  
 <span data-ttu-id="809be-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="809be-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="809be-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="809be-114">Child Elements</span></span>  
  
|<span data-ttu-id="809be-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="809be-115">Element</span></span>|<span data-ttu-id="809be-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="809be-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="809be-117">\<Servicedavranışlar ></span><span class="sxs-lookup"><span data-stu-id="809be-117">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="809be-118">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="809be-118">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="809be-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="809be-119">Parent Elements</span></span>  
  
|<span data-ttu-id="809be-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="809be-120">Element</span></span>|<span data-ttu-id="809be-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="809be-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="809be-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="809be-122">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="809be-123">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="809be-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="809be-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="809be-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="809be-125">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="809be-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
