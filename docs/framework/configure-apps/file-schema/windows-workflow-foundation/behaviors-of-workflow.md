---
title: "&lt;davranışları&gt; iş akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c1bf4beb244b72d2fe3d82d749ff6ae6723baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="060b3-102">&lt;davranışları&gt; iş akışı</span><span class="sxs-lookup"><span data-stu-id="060b3-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="060b3-103">Bu öğeyi içeren **serviceBehaviors** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="060b3-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="060b3-104">Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="060b3-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="060b3-105">Her davranış öğesi kendi benzersiz tanımlanır **adı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="060b3-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="060b3-106">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="060b3-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060b3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="060b3-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="060b3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="060b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="060b3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="060b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="060b3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="060b3-110">Attributes</span></span>  
 <span data-ttu-id="060b3-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="060b3-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="060b3-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="060b3-112">Child Elements</span></span>  
  
|<span data-ttu-id="060b3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="060b3-113">Element</span></span>|<span data-ttu-id="060b3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="060b3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="060b3-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="060b3-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="060b3-116">Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="060b3-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="060b3-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="060b3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="060b3-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="060b3-118">Element</span></span>|<span data-ttu-id="060b3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="060b3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="060b3-120">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="060b3-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="060b3-121">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="060b3-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="060b3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="060b3-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="060b3-123">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="060b3-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
