---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 16d4546bce461b55695e0deed093396ce1c2b0b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189571"
---
# \<bufferReceive>

<span data-ttu-id="7f06e-101">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="7f06e-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="7f06e-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f06e-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f06e-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f06e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7f06e-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7f06e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f06e-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7f06e-105">Attributes</span></span>  
  
|<span data-ttu-id="7f06e-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7f06e-106">Attribute</span></span>|<span data-ttu-id="7f06e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f06e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f06e-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="7f06e-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="7f06e-109">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7f06e-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="7f06e-110">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="7f06e-110">The default value is 512.</span></span> <span data-ttu-id="7f06e-111">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="7f06e-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f06e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f06e-112">Child Elements</span></span>  

 <span data-ttu-id="7f06e-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="7f06e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f06e-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f06e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7f06e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f06e-115">Element</span></span>|<span data-ttu-id="7f06e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f06e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f06e-117">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7f06e-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7f06e-118">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f06e-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f06e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f06e-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
