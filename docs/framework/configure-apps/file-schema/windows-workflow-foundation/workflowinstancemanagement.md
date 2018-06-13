---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: d86b0f61c6741fa156e04da75a62853f459324d1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767108"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="3ead8-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="3ead8-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="3ead8-103">Nasıl iş akışı örnekleri, Kalıcılık, işlenmemiş özel durum davranışını ve boşta davranışı dahil olmak üzere çalıştığını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="3ead8-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="3ead8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ead8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ead8-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="3ead8-105">\<behaviors></span></span>  
<span data-ttu-id="3ead8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3ead8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3ead8-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="3ead8-107">\<behavior></span></span>  
<span data-ttu-id="3ead8-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="3ead8-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ead8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ead8-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ead8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ead8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ead8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ead8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ead8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ead8-112">Attributes</span></span>  
  
|<span data-ttu-id="3ead8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3ead8-113">Attribute</span></span>|<span data-ttu-id="3ead8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ead8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ead8-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="3ead8-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="3ead8-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ead8-116">Child Elements</span></span>  
 <span data-ttu-id="3ead8-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ead8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ead8-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ead8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3ead8-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ead8-119">Element</span></span>|<span data-ttu-id="3ead8-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ead8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ead8-121">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3ead8-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3ead8-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ead8-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ead8-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ead8-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
