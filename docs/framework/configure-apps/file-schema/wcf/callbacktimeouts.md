---
description: 'Hakkında daha fazla bilgi edinin: <callbackTimeouts>'
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 8e2e05ad23f661c38430ccddc615c37705e6fc44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639204"
---
# \<callbackTimeouts>

<span data-ttu-id="b0972-102">Sunucudan bir çift yönlü geri çağırma sözleşmesi senaryosuna client.in için işlem akışı yaparken zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0972-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="b0972-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0972-103">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="b0972-104">Tür</span><span class="sxs-lookup"><span data-stu-id="b0972-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0972-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0972-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b0972-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0972-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0972-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0972-107">Attributes</span></span>  
  
|<span data-ttu-id="b0972-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0972-108">Attribute</span></span>|<span data-ttu-id="b0972-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0972-109">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="b0972-110"><xref:System.TimeSpan>İşlemlerin tamamlaması gereken veya otomatik olarak sonlandırılacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b0972-110">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="b0972-111">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="b0972-111">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0972-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0972-112">Child Elements</span></span>  

 <span data-ttu-id="b0972-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0972-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0972-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0972-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b0972-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0972-115">Element</span></span>|<span data-ttu-id="b0972-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0972-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b0972-117">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0972-117">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0972-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0972-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
