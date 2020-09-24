---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 92d3de42daf6f7baf288e3e74242381a60e76618
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153605"
---
# \<serviceTimeouts>

<span data-ttu-id="0b34f-101">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b34f-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="0b34f-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b34f-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="0b34f-103">Tür</span><span class="sxs-lookup"><span data-stu-id="0b34f-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b34f-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b34f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0b34f-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b34f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b34f-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b34f-106">Attributes</span></span>  
  
|<span data-ttu-id="0b34f-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b34f-107">Attribute</span></span>|<span data-ttu-id="0b34f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b34f-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="0b34f-109"><xref:System.TimeSpan>Bir işlemin istemciden sunucuya akışı gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0b34f-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="0b34f-110">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="0b34f-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b34f-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b34f-111">Child Elements</span></span>  

 <span data-ttu-id="0b34f-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0b34f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b34f-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b34f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0b34f-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b34f-114">Element</span></span>|<span data-ttu-id="0b34f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b34f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0b34f-116">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b34f-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b34f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b34f-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
