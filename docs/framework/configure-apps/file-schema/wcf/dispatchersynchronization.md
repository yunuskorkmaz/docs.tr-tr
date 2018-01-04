---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57477ea60337e5032b80bd9ae8da850099dd08f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="7599e-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="7599e-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="7599e-103">Yanıtı zaman uyumsuz olarak göndermek bir hizmet sağlayan bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7599e-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="7599e-104">\<system.serviceModel > \<davranışları > \<endpointBehaviors > \<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7599e-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="7599e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7599e-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="7599e-106">Tür</span><span class="sxs-lookup"><span data-stu-id="7599e-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="7599e-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="7599e-107">Attributes and elements</span></span>

<span data-ttu-id="7599e-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7599e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7599e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7599e-109">Attributes</span></span>

| <span data-ttu-id="7599e-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7599e-110">Attribute</span></span>               | <span data-ttu-id="7599e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7599e-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="7599e-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="7599e-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="7599e-113">Zaman uyumsuz gönderme davranışının etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7599e-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="7599e-114">Eşzamanlı sayısını alır belirten bir tamsayı kanalda verilebilir.</span><span class="sxs-lookup"><span data-stu-id="7599e-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="7599e-115">Yalnızca doğru hizmet azaltma davranışı yapılandırdıktan sonra bu değeri yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7599e-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="7599e-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="7599e-116">Child elements</span></span>

<span data-ttu-id="7599e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7599e-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7599e-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="7599e-118">Parent elements</span></span>

| <span data-ttu-id="7599e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7599e-119">Element</span></span> | <span data-ttu-id="7599e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7599e-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="7599e-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7599e-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7599e-122">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7599e-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="7599e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7599e-123">See also</span></span>

 <span data-ttu-id="7599e-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="7599e-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
