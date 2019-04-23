---
title: <behaviors> İş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129213"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="3095d-102">\<davranışlar > İş akışı</span><span class="sxs-lookup"><span data-stu-id="3095d-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="3095d-103">Bu öğeyi içeren **serviceBehaviors** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3095d-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="3095d-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3095d-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="3095d-105">Her davranışı öğesi kendi benzersiz tarafından tanımlanır **adı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3095d-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="3095d-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3095d-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3095d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3095d-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3095d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3095d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3095d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3095d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3095d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3095d-110">Attributes</span></span>  
 <span data-ttu-id="3095d-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3095d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3095d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3095d-112">Child Elements</span></span>  
  
|<span data-ttu-id="3095d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3095d-113">Element</span></span>|<span data-ttu-id="3095d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3095d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3095d-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3095d-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="3095d-116">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3095d-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3095d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3095d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3095d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3095d-118">Element</span></span>|<span data-ttu-id="3095d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3095d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3095d-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3095d-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="3095d-121">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3095d-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3095d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3095d-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="3095d-123">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="3095d-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
