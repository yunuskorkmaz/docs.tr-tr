---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398011"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="1a204-101">Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a204-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="1a204-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a204-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="1a204-103">Tür</span><span class="sxs-lookup"><span data-stu-id="1a204-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a204-104">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1a204-104">Attributes and elements</span></span>  
  
<span data-ttu-id="1a204-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a204-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a204-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a204-106">Attributes</span></span>

| <span data-ttu-id="1a204-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a204-107">Attribute</span></span>               | <span data-ttu-id="1a204-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a204-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="1a204-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="1a204-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="1a204-110">Zaman uyumsuz gönderme davranışının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a204-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="1a204-111">Kanalda verilebilirler eşzamanlı alma sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1a204-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="1a204-112">Bu değer, hizmet azaltma davranışını doğru şekilde yapılandırdıktan sonra yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a204-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="1a204-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1a204-113">Child elements</span></span>

<span data-ttu-id="1a204-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="1a204-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a204-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1a204-115">Parent elements</span></span>

| <span data-ttu-id="1a204-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a204-116">Element</span></span> | <span data-ttu-id="1a204-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a204-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1a204-118">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a204-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="1a204-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a204-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
