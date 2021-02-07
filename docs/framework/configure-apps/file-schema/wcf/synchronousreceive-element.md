---
description: 'Daha fazla bilgi edinin: <synchronousReceive> öğesi'
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: afcd10b4ad41bd6ff12dbf246f66ef7fac4e759a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682624"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="31a32-103">\<synchronousReceive> öğesi</span><span class="sxs-lookup"><span data-stu-id="31a32-103">\<synchronousReceive> element</span></span>

<span data-ttu-id="31a32-104">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti almaya yönelik çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31a32-104">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="31a32-105">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="31a32-105">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="31a32-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="31a32-106">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31a32-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31a32-107">Attributes and Elements</span></span>  

 <span data-ttu-id="31a32-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31a32-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31a32-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31a32-109">Attributes</span></span>  

 <span data-ttu-id="31a32-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="31a32-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31a32-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31a32-111">Child Elements</span></span>  

 <span data-ttu-id="31a32-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="31a32-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31a32-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31a32-113">Parent Elements</span></span>  
  
|<span data-ttu-id="31a32-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="31a32-114">Element</span></span>|<span data-ttu-id="31a32-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31a32-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="31a32-116">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="31a32-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31a32-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31a32-117">Remarks</span></span>  

 <span data-ttu-id="31a32-118">Kanal dinleyicisine varsayılan, zaman uyumsuz yerine zaman uyumlu alma kullanmasını söylemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="31a32-118">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="31a32-119">Windows Communication Foundation (WCF), kabul edilen her kanal için yeni bir iş parçacığı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="31a32-119">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="31a32-120">Çok sayıda kanal varsa, iş parçacıklarının tükenme olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="31a32-120">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a32-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31a32-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
