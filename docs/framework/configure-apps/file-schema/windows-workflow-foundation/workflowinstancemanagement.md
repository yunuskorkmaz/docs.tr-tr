---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947155"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="4334c-101">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="4334c-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="4334c-102">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="4334c-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="4334c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4334c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4334c-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4334c-104">\<behaviors></span></span>  
<span data-ttu-id="4334c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4334c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="4334c-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="4334c-106">\<behavior></span></span>  
<span data-ttu-id="4334c-107">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="4334c-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4334c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4334c-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4334c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4334c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4334c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4334c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4334c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4334c-111">Attributes</span></span>  
  
|<span data-ttu-id="4334c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4334c-112">Attribute</span></span>|<span data-ttu-id="4334c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4334c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4334c-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="4334c-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="4334c-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4334c-115">Child Elements</span></span>  
 <span data-ttu-id="4334c-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="4334c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4334c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4334c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4334c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="4334c-118">Element</span></span>|<span data-ttu-id="4334c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4334c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4334c-120">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="4334c-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4334c-121">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4334c-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4334c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4334c-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
