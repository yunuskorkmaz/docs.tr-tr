---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 2073d115dd87d513a6e48b8b585fed4b49d5bb32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157180"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="2e836-102">\<synchronousReceive> öğesi</span><span class="sxs-lookup"><span data-stu-id="2e836-102">\<synchronousReceive> element</span></span>

<span data-ttu-id="2e836-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti almaya yönelik çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e836-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="2e836-104">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2e836-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="2e836-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e836-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e836-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e836-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2e836-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e836-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e836-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e836-108">Attributes</span></span>  

 <span data-ttu-id="2e836-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e836-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e836-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e836-110">Child Elements</span></span>  

 <span data-ttu-id="2e836-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e836-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e836-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e836-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2e836-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e836-113">Element</span></span>|<span data-ttu-id="2e836-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e836-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2e836-115">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e836-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e836-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e836-116">Remarks</span></span>  

 <span data-ttu-id="2e836-117">Kanal dinleyicisine varsayılan, zaman uyumsuz yerine zaman uyumlu alma kullanmasını söylemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e836-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="2e836-118">Windows Communication Foundation (WCF), kabul edilen her kanal için yeni bir iş parçacığı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="2e836-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="2e836-119">Çok sayıda kanal varsa, iş parçacıklarının tükenme olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="2e836-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e836-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e836-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
