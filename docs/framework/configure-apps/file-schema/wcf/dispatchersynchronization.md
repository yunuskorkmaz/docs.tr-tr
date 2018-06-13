---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 34c12a05ee363df6b6cfc9ff3809bab50ee8d522
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747583"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="4cbda-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="4cbda-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="4cbda-103">Yanıtı zaman uyumsuz olarak göndermek bir hizmet sağlayan bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cbda-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="4cbda-104">\<system.serviceModel > \<davranışları > \<endpointBehaviors > \<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4cbda-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="4cbda-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cbda-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="4cbda-106">Tür</span><span class="sxs-lookup"><span data-stu-id="4cbda-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="4cbda-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4cbda-107">Attributes and elements</span></span>

<span data-ttu-id="4cbda-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4cbda-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4cbda-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4cbda-109">Attributes</span></span>

| <span data-ttu-id="4cbda-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4cbda-110">Attribute</span></span>               | <span data-ttu-id="4cbda-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cbda-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="4cbda-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="4cbda-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="4cbda-113">Zaman uyumsuz gönderme davranışının etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4cbda-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="4cbda-114">Eşzamanlı sayısını alır belirten bir tamsayı kanalda verilebilir.</span><span class="sxs-lookup"><span data-stu-id="4cbda-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="4cbda-115">Yalnızca doğru hizmet azaltma davranışı yapılandırdıktan sonra bu değeri yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4cbda-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="4cbda-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4cbda-116">Child elements</span></span>

<span data-ttu-id="4cbda-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="4cbda-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4cbda-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4cbda-118">Parent elements</span></span>

| <span data-ttu-id="4cbda-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4cbda-119">Element</span></span> | <span data-ttu-id="4cbda-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cbda-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="4cbda-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4cbda-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4cbda-122">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cbda-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4cbda-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cbda-123">See also</span></span>

 <span data-ttu-id="4cbda-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="4cbda-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
