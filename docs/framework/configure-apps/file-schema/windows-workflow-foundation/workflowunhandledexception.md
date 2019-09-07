---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398562"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="f12d5-101">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="f12d5-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="f12d5-102">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f12d5-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="f12d5-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f12d5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f12d5-104">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f12d5-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f12d5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f12d5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f12d5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f12d5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f12d5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f12d5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f12d5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowUnhandledException >**</span><span class="sxs-lookup"><span data-stu-id="f12d5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12d5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f12d5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f12d5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f12d5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f12d5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f12d5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f12d5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f12d5-112">Attributes</span></span>  
  
|<span data-ttu-id="f12d5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f12d5-113">Attribute</span></span>|<span data-ttu-id="f12d5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f12d5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f12d5-115">Eylem</span><span class="sxs-lookup"><span data-stu-id="f12d5-115">action</span></span>|<span data-ttu-id="f12d5-116">İşlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f12d5-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="f12d5-117">Bu öznitelik türü<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="f12d5-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f12d5-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f12d5-118">Child Elements</span></span>  
 <span data-ttu-id="f12d5-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="f12d5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f12d5-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f12d5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f12d5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f12d5-121">Element</span></span>|<span data-ttu-id="f12d5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f12d5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f12d5-123">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="f12d5-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f12d5-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f12d5-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f12d5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f12d5-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
