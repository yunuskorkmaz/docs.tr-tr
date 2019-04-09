---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: cfe3350ac42d1e0e837b79f25753f62dc2051dd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096257"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="7b8d6-101">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="7b8d6-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="7b8d6-102">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="7b8d6-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="7b8d6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b8d6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b8d6-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="7b8d6-104">\<behaviors></span></span>  
<span data-ttu-id="7b8d6-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7b8d6-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b8d6-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7b8d6-106">\<behavior></span></span>  
<span data-ttu-id="7b8d6-107">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="7b8d6-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b8d6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b8d6-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b8d6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b8d6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7b8d6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b8d6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b8d6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b8d6-111">Attributes</span></span>  
  
|<span data-ttu-id="7b8d6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b8d6-112">Attribute</span></span>|<span data-ttu-id="7b8d6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b8d6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b8d6-114">Eylem</span><span class="sxs-lookup"><span data-stu-id="7b8d6-114">action</span></span>|<span data-ttu-id="7b8d6-115">İşlenmeyen bir özel durum oluştuğunda yapılacak eylem belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7b8d6-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="7b8d6-116">Bu öznitelik türünde</span><span class="sxs-lookup"><span data-stu-id="7b8d6-116">This attribute is of type</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b8d6-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b8d6-117">Child Elements</span></span>  
 <span data-ttu-id="7b8d6-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b8d6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b8d6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b8d6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b8d6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b8d6-120">Element</span></span>|<span data-ttu-id="7b8d6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b8d6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b8d6-122">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7b8d6-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7b8d6-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b8d6-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b8d6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b8d6-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
