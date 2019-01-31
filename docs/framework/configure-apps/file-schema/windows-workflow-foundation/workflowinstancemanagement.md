---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: baa1ccbe0accd2db701fac9ef53cdc6357713c5d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257427"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="57593-101">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="57593-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="57593-102">Nasıl iş akışı örnekleri, Kalıcılık, İşlenmeyen özel durum davranışını ve boşta davranışlarını çalıştırılır denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="57593-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="57593-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="57593-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="57593-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="57593-104">\<behaviors></span></span>  
<span data-ttu-id="57593-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="57593-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="57593-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="57593-106">\<behavior></span></span>  
<span data-ttu-id="57593-107">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="57593-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57593-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57593-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57593-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57593-109">Attributes and Elements</span></span>  
 <span data-ttu-id="57593-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57593-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57593-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57593-111">Attributes</span></span>  
  
|<span data-ttu-id="57593-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57593-112">Attribute</span></span>|<span data-ttu-id="57593-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57593-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57593-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="57593-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="57593-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57593-115">Child Elements</span></span>  
 <span data-ttu-id="57593-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="57593-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57593-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57593-117">Parent Elements</span></span>  
  
|<span data-ttu-id="57593-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="57593-118">Element</span></span>|<span data-ttu-id="57593-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57593-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57593-120">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="57593-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="57593-121">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="57593-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57593-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57593-122">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
