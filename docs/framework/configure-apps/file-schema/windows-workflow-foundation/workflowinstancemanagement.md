---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397528"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="18390-101">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="18390-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="18390-102">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="18390-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="18390-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="18390-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="18390-104">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="18390-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="18390-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="18390-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="18390-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="18390-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="18390-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="18390-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="18390-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceManagement >**</span><span class="sxs-lookup"><span data-stu-id="18390-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18390-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18390-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18390-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="18390-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18390-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18390-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18390-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18390-112">Attributes</span></span>  
  
|<span data-ttu-id="18390-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="18390-113">Attribute</span></span>|<span data-ttu-id="18390-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18390-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18390-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="18390-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="18390-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="18390-116">Child Elements</span></span>  
 <span data-ttu-id="18390-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="18390-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18390-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="18390-118">Parent Elements</span></span>  
  
|<span data-ttu-id="18390-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="18390-119">Element</span></span>|<span data-ttu-id="18390-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18390-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18390-121">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="18390-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="18390-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="18390-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18390-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18390-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
