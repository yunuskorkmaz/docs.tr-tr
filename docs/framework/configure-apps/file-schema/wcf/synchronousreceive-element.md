---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399506"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="1eee8-102">\<synchronousReceive> öğesi</span><span class="sxs-lookup"><span data-stu-id="1eee8-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="1eee8-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti almaya yönelik çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1eee8-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="1eee8-104">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1eee8-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="1eee8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1eee8-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1eee8-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1eee8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1eee8-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1eee8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1eee8-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1eee8-108">Attributes</span></span>  
 <span data-ttu-id="1eee8-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="1eee8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1eee8-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1eee8-110">Child Elements</span></span>  
 <span data-ttu-id="1eee8-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="1eee8-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1eee8-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1eee8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1eee8-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="1eee8-113">Element</span></span>|<span data-ttu-id="1eee8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1eee8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1eee8-115">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1eee8-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eee8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1eee8-116">Remarks</span></span>  
 <span data-ttu-id="1eee8-117">Kanal dinleyicisine varsayılan, zaman uyumsuz yerine zaman uyumlu alma kullanmasını söylemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1eee8-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="1eee8-118">Windows Communication Foundation (WCF), kabul edilen her kanal için yeni bir iş parçacığı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="1eee8-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="1eee8-119">Çok sayıda kanal varsa, iş parçacıklarının tükenme olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="1eee8-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eee8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1eee8-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
