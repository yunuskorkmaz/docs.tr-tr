---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 6ed37d73440dac22288ae1da526d81b2d0b990a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286630"
---
# <a name="bufferreceive"></a><span data-ttu-id="228a9-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="228a9-101">\<bufferReceive></span></span>
<span data-ttu-id="228a9-102">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="228a9-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="228a9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="228a9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="228a9-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="228a9-104">\<behaviors></span></span>  
<span data-ttu-id="228a9-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="228a9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="228a9-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="228a9-106">\<behavior></span></span>  
<span data-ttu-id="228a9-107">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="228a9-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228a9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="228a9-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="228a9-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="228a9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="228a9-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="228a9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="228a9-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="228a9-111">Attributes</span></span>  
  
|<span data-ttu-id="228a9-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="228a9-112">Attribute</span></span>|<span data-ttu-id="228a9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="228a9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="228a9-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="228a9-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="228a9-115">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="228a9-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="228a9-116">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="228a9-116">The default value is 512.</span></span> <span data-ttu-id="228a9-117">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="228a9-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="228a9-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="228a9-118">Child Elements</span></span>  
 <span data-ttu-id="228a9-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="228a9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="228a9-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="228a9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="228a9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="228a9-121">Element</span></span>|<span data-ttu-id="228a9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="228a9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="228a9-123">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="228a9-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="228a9-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="228a9-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="228a9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="228a9-125">See also</span></span>
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
