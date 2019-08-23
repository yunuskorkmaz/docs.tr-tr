---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 1d4611d6fee9dad057985f7d8f5ef961d384efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945967"
---
# <a name="bufferreceive"></a><span data-ttu-id="2f3d9-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="2f3d9-101">\<bufferReceive></span></span>
<span data-ttu-id="2f3d9-102">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="2f3d9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2f3d9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2f3d9-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2f3d9-104">\<behaviors></span></span>  
<span data-ttu-id="2f3d9-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2f3d9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2f3d9-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="2f3d9-106">\<behavior></span></span>  
<span data-ttu-id="2f3d9-107">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="2f3d9-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3d9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f3d9-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f3d9-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f3d9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2f3d9-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f3d9-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2f3d9-111">Attributes</span></span>  
  
|<span data-ttu-id="2f3d9-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2f3d9-112">Attribute</span></span>|<span data-ttu-id="2f3d9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f3d9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f3d9-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="2f3d9-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="2f3d9-115">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="2f3d9-116">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-116">The default value is 512.</span></span> <span data-ttu-id="2f3d9-117">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f3d9-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f3d9-118">Child Elements</span></span>  
 <span data-ttu-id="2f3d9-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f3d9-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f3d9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2f3d9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2f3d9-121">Element</span></span>|<span data-ttu-id="2f3d9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f3d9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f3d9-123">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="2f3d9-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="2f3d9-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f3d9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f3d9-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
