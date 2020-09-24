---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 532d4c31a582b2b0cd90f6f42b20e00790f9ab02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148665"
---
# \<workflowInstanceManagement>

<span data-ttu-id="0d32d-101">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="0d32d-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="0d32d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d32d-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d32d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d32d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0d32d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0d32d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d32d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d32d-105">Attributes</span></span>  
  
|<span data-ttu-id="0d32d-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0d32d-106">Attribute</span></span>|<span data-ttu-id="0d32d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d32d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d32d-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="0d32d-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="0d32d-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d32d-109">Child Elements</span></span>  

 <span data-ttu-id="0d32d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d32d-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d32d-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d32d-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0d32d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d32d-112">Element</span></span>|<span data-ttu-id="0d32d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d32d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d32d-114">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0d32d-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0d32d-115">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d32d-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d32d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d32d-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
