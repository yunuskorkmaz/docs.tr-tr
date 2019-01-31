---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: caf5be7aaff0df436be3a1d618a9f89bb32e6bb7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254858"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="f34f7-101">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="f34f7-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="f34f7-102">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f34f7-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="f34f7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f34f7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f34f7-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f34f7-104">\<behaviors></span></span>  
<span data-ttu-id="f34f7-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f34f7-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f34f7-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f34f7-106">\<behavior></span></span>  
<span data-ttu-id="f34f7-107">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="f34f7-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34f7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f34f7-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f34f7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f34f7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f34f7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f34f7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f34f7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f34f7-111">Attributes</span></span>  
  
|<span data-ttu-id="f34f7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f34f7-112">Attribute</span></span>|<span data-ttu-id="f34f7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f34f7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f34f7-114">Eylem</span><span class="sxs-lookup"><span data-stu-id="f34f7-114">action</span></span>|<span data-ttu-id="f34f7-115">İşlenmeyen bir özel durum oluştuğunda yapılacak eylem belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f34f7-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="f34f7-116">Bu öznitelik türünde <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="f34f7-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f34f7-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f34f7-117">Child Elements</span></span>  
 <span data-ttu-id="f34f7-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="f34f7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f34f7-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f34f7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f34f7-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f34f7-120">Element</span></span>|<span data-ttu-id="f34f7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f34f7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f34f7-122">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f34f7-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f34f7-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f34f7-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f34f7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f34f7-124">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
