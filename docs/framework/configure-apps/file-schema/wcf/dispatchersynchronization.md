---
description: 'Hakkında daha fazla bilgi edinin: <dispatcherSynchronization>'
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 93664dec3648ed58df7e3e5c0760f1694c60ba7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749628"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="b2624-102">Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2624-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="b2624-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2624-103">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="b2624-104">Tür</span><span class="sxs-lookup"><span data-stu-id="b2624-104">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2624-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b2624-105">Attributes and elements</span></span>  
  
<span data-ttu-id="b2624-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2624-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2624-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2624-107">Attributes</span></span>

| <span data-ttu-id="b2624-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b2624-108">Attribute</span></span>               | <span data-ttu-id="b2624-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2624-109">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="b2624-110">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="b2624-110">asynchronousSendEnabled</span></span> | <span data-ttu-id="b2624-111">Zaman uyumsuz gönderme davranışının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b2624-111">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="b2624-112">Kanalda verilebilirler eşzamanlı alma sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b2624-112">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="b2624-113">Bu değer, hizmet azaltma davranışını doğru şekilde yapılandırdıktan sonra yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2624-113">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="b2624-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b2624-114">Child elements</span></span>

<span data-ttu-id="b2624-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2624-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2624-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b2624-116">Parent elements</span></span>

| <span data-ttu-id="b2624-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2624-117">Element</span></span> | <span data-ttu-id="b2624-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2624-118">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b2624-119">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2624-119">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b2624-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2624-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
