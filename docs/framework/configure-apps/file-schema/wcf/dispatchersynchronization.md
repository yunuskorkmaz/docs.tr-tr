---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398011"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="15b6f-101">\<dispatcherSynchronization ></span><span class="sxs-lookup"><span data-stu-id="15b6f-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="15b6f-102">Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="15b6f-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="15b6f-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="15b6f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="15b6f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="15b6f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="15b6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="15b6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="15b6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="15b6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="15b6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="15b6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="15b6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**</span><span class="sxs-lookup"><span data-stu-id="15b6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b6f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15b6f-109">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="15b6f-110">Tür</span><span class="sxs-lookup"><span data-stu-id="15b6f-110">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15b6f-111">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="15b6f-111">Attributes and elements</span></span>  
  
<span data-ttu-id="15b6f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15b6f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15b6f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15b6f-113">Attributes</span></span>

| <span data-ttu-id="15b6f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15b6f-114">Attribute</span></span>               | <span data-ttu-id="15b6f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15b6f-115">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="15b6f-116">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="15b6f-116">asynchronousSendEnabled</span></span> | <span data-ttu-id="15b6f-117">Zaman uyumsuz gönderme davranışının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="15b6f-117">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="15b6f-118">Kanalda verilebilirler eşzamanlı alma sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="15b6f-118">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="15b6f-119">Bu değer, hizmet azaltma davranışını doğru şekilde yapılandırdıktan sonra yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15b6f-119">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="15b6f-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="15b6f-120">Child elements</span></span>

<span data-ttu-id="15b6f-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="15b6f-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15b6f-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="15b6f-122">Parent elements</span></span>

| <span data-ttu-id="15b6f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="15b6f-123">Element</span></span> | <span data-ttu-id="15b6f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15b6f-124">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="15b6f-125">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="15b6f-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="15b6f-126">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="15b6f-126">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="15b6f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15b6f-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
