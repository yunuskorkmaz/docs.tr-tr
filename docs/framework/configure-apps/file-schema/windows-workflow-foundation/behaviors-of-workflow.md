---
title: '&lt;davranışlar&gt; iş akışı'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b4ad7fb54cc8a03f5dd698055da5a29e719775c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731679"
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="99577-102">&lt;davranışlar&gt; iş akışı</span><span class="sxs-lookup"><span data-stu-id="99577-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="99577-103">Bu öğeyi içeren **serviceBehaviors** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="99577-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="99577-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99577-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="99577-105">Her davranışı öğesi kendi benzersiz tarafından tanımlanır **adı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="99577-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="99577-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99577-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99577-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99577-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99577-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99577-108">Attributes and Elements</span></span>  
 <span data-ttu-id="99577-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99577-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99577-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99577-110">Attributes</span></span>  
 <span data-ttu-id="99577-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="99577-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99577-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99577-112">Child Elements</span></span>  
  
|<span data-ttu-id="99577-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="99577-113">Element</span></span>|<span data-ttu-id="99577-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99577-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99577-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="99577-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="99577-116">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99577-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99577-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99577-117">Parent Elements</span></span>  
  
|<span data-ttu-id="99577-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="99577-118">Element</span></span>|<span data-ttu-id="99577-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99577-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99577-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99577-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="99577-121">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="99577-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99577-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99577-122">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="99577-123">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="99577-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
