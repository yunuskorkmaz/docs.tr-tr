---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398841"
---
# \<bufferReceive>
<span data-ttu-id="0ecea-101">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="0ecea-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="0ecea-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ecea-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ecea-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ecea-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0ecea-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ecea-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ecea-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ecea-105">Attributes</span></span>  
  
|<span data-ttu-id="0ecea-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ecea-106">Attribute</span></span>|<span data-ttu-id="0ecea-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ecea-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ecea-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="0ecea-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="0ecea-109">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0ecea-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="0ecea-110">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="0ecea-110">The default value is 512.</span></span> <span data-ttu-id="0ecea-111">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="0ecea-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ecea-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ecea-112">Child Elements</span></span>  
 <span data-ttu-id="0ecea-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ecea-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ecea-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ecea-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0ecea-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ecea-115">Element</span></span>|<span data-ttu-id="0ecea-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ecea-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ecea-117">\<behavior>durumunu\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0ecea-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0ecea-118">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ecea-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ecea-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ecea-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
