---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397528"
---
# \<workflowInstanceManagement>
<span data-ttu-id="9da3e-101">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9da3e-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="9da3e-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9da3e-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9da3e-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9da3e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9da3e-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9da3e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9da3e-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9da3e-105">Attributes</span></span>  
  
|<span data-ttu-id="9da3e-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9da3e-106">Attribute</span></span>|<span data-ttu-id="9da3e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9da3e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9da3e-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="9da3e-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="9da3e-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9da3e-109">Child Elements</span></span>  
 <span data-ttu-id="9da3e-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="9da3e-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9da3e-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9da3e-111">Parent Elements</span></span>  
  
|<span data-ttu-id="9da3e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9da3e-112">Element</span></span>|<span data-ttu-id="9da3e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9da3e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9da3e-114">\<behavior>durumunu\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9da3e-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9da3e-115">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9da3e-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9da3e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9da3e-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
