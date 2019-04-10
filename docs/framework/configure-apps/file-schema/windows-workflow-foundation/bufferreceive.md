---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 360d26fda964fa33640e833ad22dab7e06e153f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203164"
---
# <a name="bufferreceive"></a><span data-ttu-id="a7579-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="a7579-101">\<bufferReceive></span></span>
<span data-ttu-id="a7579-102">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a7579-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="a7579-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7579-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7579-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a7579-104">\<behaviors></span></span>  
<span data-ttu-id="a7579-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a7579-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a7579-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a7579-106">\<behavior></span></span>  
<span data-ttu-id="a7579-107">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="a7579-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7579-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7579-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7579-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7579-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7579-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7579-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7579-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7579-111">Attributes</span></span>  
  
|<span data-ttu-id="a7579-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7579-112">Attribute</span></span>|<span data-ttu-id="a7579-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7579-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7579-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="a7579-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="a7579-115">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a7579-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="a7579-116">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="a7579-116">The default value is 512.</span></span> <span data-ttu-id="a7579-117">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="a7579-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7579-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7579-118">Child Elements</span></span>  
 <span data-ttu-id="a7579-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7579-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7579-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7579-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a7579-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7579-121">Element</span></span>|<span data-ttu-id="a7579-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7579-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7579-123">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a7579-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a7579-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7579-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7579-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7579-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
