---
description: 'Hakkında daha fazla bilgi edinin: <workflowUnhandledException>'
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: b9258c986ffa154e490f80bead1dc53d8f7ef44d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697783"
---
# \<workflowUnhandledException>

<span data-ttu-id="8765e-102">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="8765e-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="8765e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="8765e-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8765e-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8765e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8765e-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8765e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8765e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8765e-106">Attributes</span></span>  
  
|<span data-ttu-id="8765e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8765e-107">Attribute</span></span>|<span data-ttu-id="8765e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8765e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8765e-109">eylem</span><span class="sxs-lookup"><span data-stu-id="8765e-109">action</span></span>|<span data-ttu-id="8765e-110">İşlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8765e-110">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="8765e-111">Bu öznitelik türü <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="8765e-111">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8765e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8765e-112">Child Elements</span></span>  

 <span data-ttu-id="8765e-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="8765e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8765e-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8765e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8765e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="8765e-115">Element</span></span>|<span data-ttu-id="8765e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8765e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8765e-117">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8765e-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8765e-118">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8765e-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8765e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8765e-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
