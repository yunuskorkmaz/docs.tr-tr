---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 537dee408f1af29a06042de439a2c1e7d7874222
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555394"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="46e38-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="46e38-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="46e38-103">Zaman uyumsuz yanıtlar göndermek bir hizmet sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="46e38-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="46e38-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="46e38-104">\<system.serviceModel></span></span>  
<span data-ttu-id="46e38-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="46e38-105">\<behaviors></span></span>  
<span data-ttu-id="46e38-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="46e38-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="46e38-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="46e38-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e38-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46e38-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="46e38-109">Tür</span><span class="sxs-lookup"><span data-stu-id="46e38-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46e38-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="46e38-110">Attributes and elements</span></span>  
  
<span data-ttu-id="46e38-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46e38-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46e38-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46e38-112">Attributes</span></span>

| <span data-ttu-id="46e38-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="46e38-113">Attribute</span></span>               | <span data-ttu-id="46e38-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46e38-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="46e38-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="46e38-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="46e38-116">Zaman uyumsuz gönderme davranışının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="46e38-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="46e38-117">Kanal sayısı eşzamanlı alımların belirten bir tamsayı verilebilir.</span><span class="sxs-lookup"><span data-stu-id="46e38-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="46e38-118">Bu değer yalnızca doğru hizmet azaltma davranışı yapılandırdıktan sonra yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46e38-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="46e38-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="46e38-119">Child elements</span></span>

<span data-ttu-id="46e38-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="46e38-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46e38-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="46e38-121">Parent elements</span></span>

| <span data-ttu-id="46e38-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="46e38-122">Element</span></span> | <span data-ttu-id="46e38-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46e38-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="46e38-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="46e38-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="46e38-125">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="46e38-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="46e38-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46e38-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
