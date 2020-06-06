---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398562"
---
# \<workflowUnhandledException>
<span data-ttu-id="65958-101">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="65958-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="65958-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65958-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65958-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="65958-103">Attributes and Elements</span></span>  
 <span data-ttu-id="65958-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65958-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65958-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65958-105">Attributes</span></span>  
  
|<span data-ttu-id="65958-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="65958-106">Attribute</span></span>|<span data-ttu-id="65958-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65958-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65958-108">action</span><span class="sxs-lookup"><span data-stu-id="65958-108">action</span></span>|<span data-ttu-id="65958-109">İşlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="65958-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="65958-110">Bu öznitelik türü<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="65958-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65958-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="65958-111">Child Elements</span></span>  
 <span data-ttu-id="65958-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="65958-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65958-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="65958-113">Parent Elements</span></span>  
  
|<span data-ttu-id="65958-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="65958-114">Element</span></span>|<span data-ttu-id="65958-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65958-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65958-116">\<behavior>durumunu\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="65958-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="65958-117">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="65958-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65958-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65958-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
