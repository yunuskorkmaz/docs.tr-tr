---
description: 'Hakkında daha fazla bilgi edinin: <bufferReceive>'
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 8f5e58e0e72a81d8b3a20a68e0890be907c20d2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698095"
---
# \<bufferReceive>

<span data-ttu-id="291ee-102">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="291ee-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="291ee-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="291ee-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="291ee-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="291ee-104">Attributes and Elements</span></span>  

 <span data-ttu-id="291ee-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="291ee-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="291ee-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="291ee-106">Attributes</span></span>  
  
|<span data-ttu-id="291ee-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="291ee-107">Attribute</span></span>|<span data-ttu-id="291ee-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="291ee-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="291ee-109">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="291ee-109">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="291ee-110">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="291ee-110">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="291ee-111">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="291ee-111">The default value is 512.</span></span> <span data-ttu-id="291ee-112">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="291ee-112">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="291ee-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="291ee-113">Child Elements</span></span>  

 <span data-ttu-id="291ee-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="291ee-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="291ee-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="291ee-115">Parent Elements</span></span>  
  
|<span data-ttu-id="291ee-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="291ee-116">Element</span></span>|<span data-ttu-id="291ee-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="291ee-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="291ee-118">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="291ee-118">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="291ee-119">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="291ee-119">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="291ee-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="291ee-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
