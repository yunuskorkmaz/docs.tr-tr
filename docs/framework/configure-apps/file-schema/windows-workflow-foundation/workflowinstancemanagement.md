---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191620"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="4252b-101">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="4252b-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="4252b-102">Nasıl iş akışı örnekleri, Kalıcılık, İşlenmeyen özel durum davranışını ve boşta davranışlarını çalıştırılır denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="4252b-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="4252b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4252b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4252b-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4252b-104">\<behaviors></span></span>  
<span data-ttu-id="4252b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4252b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="4252b-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4252b-106">\<behavior></span></span>  
<span data-ttu-id="4252b-107">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="4252b-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4252b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4252b-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4252b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4252b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4252b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4252b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4252b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4252b-111">Attributes</span></span>  
  
|<span data-ttu-id="4252b-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4252b-112">Attribute</span></span>|<span data-ttu-id="4252b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4252b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4252b-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="4252b-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="4252b-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4252b-115">Child Elements</span></span>  
 <span data-ttu-id="4252b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="4252b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4252b-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4252b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4252b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="4252b-118">Element</span></span>|<span data-ttu-id="4252b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4252b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4252b-120">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4252b-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4252b-121">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4252b-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4252b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4252b-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
