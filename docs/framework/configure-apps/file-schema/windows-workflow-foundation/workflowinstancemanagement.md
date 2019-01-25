---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: ba3d9415efc21012b470fd2e9a7f426ca8f3aad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662068"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="fc5b5-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="fc5b5-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="fc5b5-103">Nasıl iş akışı örnekleri, Kalıcılık, İşlenmeyen özel durum davranışını ve boşta davranışlarını çalıştırılır denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="fc5b5-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="fc5b5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fc5b5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fc5b5-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="fc5b5-105">\<behaviors></span></span>  
<span data-ttu-id="fc5b5-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fc5b5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fc5b5-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fc5b5-107">\<behavior></span></span>  
<span data-ttu-id="fc5b5-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="fc5b5-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc5b5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc5b5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc5b5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc5b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fc5b5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc5b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc5b5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc5b5-112">Attributes</span></span>  
  
|<span data-ttu-id="fc5b5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc5b5-113">Attribute</span></span>|<span data-ttu-id="fc5b5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc5b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc5b5-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="fc5b5-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="fc5b5-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc5b5-116">Child Elements</span></span>  
 <span data-ttu-id="fc5b5-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc5b5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc5b5-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc5b5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fc5b5-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc5b5-119">Element</span></span>|<span data-ttu-id="fc5b5-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc5b5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc5b5-121">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fc5b5-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fc5b5-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc5b5-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc5b5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc5b5-123">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
