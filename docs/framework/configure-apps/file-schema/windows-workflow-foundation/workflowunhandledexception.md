---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: c46d1fb9eb853e57c7ad1b97eb9a22556cdfb7d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913106"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="c21da-101">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="c21da-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="c21da-102">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="c21da-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="c21da-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c21da-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c21da-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c21da-104">\<behaviors></span></span>  
<span data-ttu-id="c21da-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c21da-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c21da-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c21da-106">\<behavior></span></span>  
<span data-ttu-id="c21da-107">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="c21da-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c21da-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c21da-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c21da-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c21da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c21da-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c21da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c21da-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c21da-111">Attributes</span></span>  
  
|<span data-ttu-id="c21da-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c21da-112">Attribute</span></span>|<span data-ttu-id="c21da-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c21da-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c21da-114">Eylem</span><span class="sxs-lookup"><span data-stu-id="c21da-114">action</span></span>|<span data-ttu-id="c21da-115">İşlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c21da-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="c21da-116">Bu öznitelik türü<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="c21da-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c21da-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c21da-117">Child Elements</span></span>  
 <span data-ttu-id="c21da-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="c21da-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c21da-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c21da-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c21da-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="c21da-120">Element</span></span>|<span data-ttu-id="c21da-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c21da-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c21da-122">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="c21da-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c21da-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c21da-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c21da-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c21da-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
