---
title: <behaviors> iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 21974f77526f55a47c014a285efd3bbac6fc1f7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189610"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="ad124-102">\<behaviors> iş akışı</span><span class="sxs-lookup"><span data-stu-id="ad124-102">\<behaviors> of workflow</span></span>

<span data-ttu-id="ad124-103">Bu öğe **Servicedavranışlar** koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ad124-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="ad124-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad124-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="ad124-105">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ad124-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="ad124-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad124-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad124-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad124-107">Attributes and Elements</span></span>  

 <span data-ttu-id="ad124-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad124-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad124-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad124-109">Attributes</span></span>  

 <span data-ttu-id="ad124-110">Yok</span><span class="sxs-lookup"><span data-stu-id="ad124-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad124-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad124-111">Child Elements</span></span>  
  
|<span data-ttu-id="ad124-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad124-112">Element</span></span>|<span data-ttu-id="ad124-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad124-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="ad124-114">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ad124-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad124-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad124-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ad124-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad124-116">Element</span></span>|<span data-ttu-id="ad124-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad124-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="ad124-118">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ad124-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad124-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad124-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="ad124-120">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="ad124-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
