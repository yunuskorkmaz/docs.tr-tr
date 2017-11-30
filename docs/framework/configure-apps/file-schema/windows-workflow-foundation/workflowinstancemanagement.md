---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9883cedbbe3657eb82c25abbad66487e39ce2579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="8fa6e-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="8fa6e-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="8fa6e-103">Nasıl iş akışı örnekleri, Kalıcılık, işlenmemiş özel durum davranışını ve boşta davranışı dahil olmak üzere çalıştığını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="8fa6e-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8fa6e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8fa6e-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="8fa6e-105">\<behaviors></span></span>  
<span data-ttu-id="8fa6e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8fa6e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8fa6e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8fa6e-107">\<behavior></span></span>  
<span data-ttu-id="8fa6e-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="8fa6e-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa6e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fa6e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fa6e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fa6e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8fa6e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fa6e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8fa6e-112">Attributes</span></span>  
  
|<span data-ttu-id="8fa6e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8fa6e-113">Attribute</span></span>|<span data-ttu-id="8fa6e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fa6e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fa6e-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="8fa6e-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="8fa6e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fa6e-116">Child Elements</span></span>  
 <span data-ttu-id="8fa6e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8fa6e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fa6e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8fa6e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fa6e-119">Element</span></span>|<span data-ttu-id="8fa6e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fa6e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fa6e-121">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8fa6e-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8fa6e-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fa6e-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
