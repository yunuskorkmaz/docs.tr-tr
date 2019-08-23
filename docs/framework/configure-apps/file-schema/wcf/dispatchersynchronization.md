---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925851"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="6e32b-101">\<dispatcherSynchronization ></span><span class="sxs-lookup"><span data-stu-id="6e32b-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="6e32b-102">Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e32b-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="6e32b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6e32b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6e32b-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6e32b-104">\<behaviors></span></span>  
<span data-ttu-id="6e32b-105">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="6e32b-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="6e32b-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6e32b-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e32b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e32b-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="6e32b-108">Tür</span><span class="sxs-lookup"><span data-stu-id="6e32b-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e32b-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6e32b-109">Attributes and elements</span></span>  
  
<span data-ttu-id="6e32b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e32b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e32b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e32b-111">Attributes</span></span>

| <span data-ttu-id="6e32b-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e32b-112">Attribute</span></span>               | <span data-ttu-id="6e32b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e32b-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="6e32b-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="6e32b-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="6e32b-115">Zaman uyumsuz gönderme davranışının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6e32b-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="6e32b-116">Kanalda verilebilirler eşzamanlı alma sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6e32b-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="6e32b-117">Bu değer, hizmet azaltma davranışını doğru şekilde yapılandırdıktan sonra yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e32b-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="6e32b-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6e32b-118">Child elements</span></span>

<span data-ttu-id="6e32b-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e32b-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6e32b-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6e32b-120">Parent elements</span></span>

| <span data-ttu-id="6e32b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e32b-121">Element</span></span> | <span data-ttu-id="6e32b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e32b-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="6e32b-123">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6e32b-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6e32b-124">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e32b-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6e32b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e32b-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
