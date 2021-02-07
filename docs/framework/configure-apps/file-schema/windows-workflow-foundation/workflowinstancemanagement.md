---
description: 'Hakkında daha fazla bilgi edinin: <workflowInstanceManagement>'
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 528c0c923be93d9581b8e3bfccc382eab11c5da1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697926"
---
# \<workflowInstanceManagement>

<span data-ttu-id="6c873-102">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="6c873-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="6c873-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c873-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c873-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c873-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6c873-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c873-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c873-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c873-106">Attributes</span></span>  
  
|<span data-ttu-id="6c873-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c873-107">Attribute</span></span>|<span data-ttu-id="6c873-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c873-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c873-109">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="6c873-109">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="6c873-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c873-110">Child Elements</span></span>  

 <span data-ttu-id="6c873-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c873-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c873-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c873-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6c873-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c873-113">Element</span></span>|<span data-ttu-id="6c873-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c873-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c873-115">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6c873-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6c873-116">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c873-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c873-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c873-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
