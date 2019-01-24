---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 5c5dddc6d126811d7fd1eaae2f85df1e42c1cd41
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700877"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="5bfb8-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="5bfb8-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="5bfb8-103">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="5bfb8-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="5bfb8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5bfb8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5bfb8-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="5bfb8-105">\<behaviors></span></span>  
<span data-ttu-id="5bfb8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5bfb8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5bfb8-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5bfb8-107">\<behavior></span></span>  
<span data-ttu-id="5bfb8-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="5bfb8-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfb8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bfb8-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bfb8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bfb8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5bfb8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5bfb8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bfb8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5bfb8-112">Attributes</span></span>  
  
|<span data-ttu-id="5bfb8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5bfb8-113">Attribute</span></span>|<span data-ttu-id="5bfb8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bfb8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bfb8-115">Eylem</span><span class="sxs-lookup"><span data-stu-id="5bfb8-115">action</span></span>|<span data-ttu-id="5bfb8-116">İşlenmeyen bir özel durum oluştuğunda yapılacak eylem belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5bfb8-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="5bfb8-117">Bu öznitelik türünde <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="5bfb8-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bfb8-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bfb8-118">Child Elements</span></span>  
 <span data-ttu-id="5bfb8-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="5bfb8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bfb8-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bfb8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5bfb8-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="5bfb8-121">Element</span></span>|<span data-ttu-id="5bfb8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bfb8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bfb8-123">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5bfb8-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5bfb8-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bfb8-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bfb8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bfb8-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
