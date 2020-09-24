---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 6e3993e43aac746f380a30341fe4ebffcd257c5f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148522"
---
# \<workflowUnhandledException>

<span data-ttu-id="0ac23-101">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="0ac23-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="0ac23-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ac23-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ac23-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ac23-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0ac23-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ac23-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ac23-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ac23-105">Attributes</span></span>  
  
|<span data-ttu-id="0ac23-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ac23-106">Attribute</span></span>|<span data-ttu-id="0ac23-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ac23-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ac23-108">eylem</span><span class="sxs-lookup"><span data-stu-id="0ac23-108">action</span></span>|<span data-ttu-id="0ac23-109">İşlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0ac23-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="0ac23-110">Bu öznitelik türü <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="0ac23-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ac23-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ac23-111">Child Elements</span></span>  

 <span data-ttu-id="0ac23-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ac23-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ac23-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ac23-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0ac23-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ac23-114">Element</span></span>|<span data-ttu-id="0ac23-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ac23-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ac23-116">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0ac23-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0ac23-117">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ac23-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ac23-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ac23-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
