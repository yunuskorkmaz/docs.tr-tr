---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398192"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="7a195-101">\<Callbackzamanaşımları ></span><span class="sxs-lookup"><span data-stu-id="7a195-101">\<callbackTimeouts></span></span>
<span data-ttu-id="7a195-102">Sunucudan bir çift yönlü geri çağırma sözleşmesi senaryosuna client.in için işlem akışı yaparken zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a195-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
<span data-ttu-id="7a195-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a195-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a195-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7a195-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7a195-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7a195-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7a195-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7a195-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7a195-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7a195-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7a195-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Callbackzamanaşımları >**</span><span class="sxs-lookup"><span data-stu-id="7a195-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a195-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a195-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="7a195-110">Tür</span><span class="sxs-lookup"><span data-stu-id="7a195-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a195-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a195-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7a195-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a195-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a195-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a195-113">Attributes</span></span>  
  
|<span data-ttu-id="7a195-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7a195-114">Attribute</span></span>|<span data-ttu-id="7a195-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a195-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="7a195-116">İşlemlerin <xref:System.TimeSpan> tamamlaması gereken veya otomatik olarak sonlandırılacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7a195-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="7a195-117">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="7a195-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a195-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a195-118">Child Elements</span></span>  
 <span data-ttu-id="7a195-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="7a195-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a195-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a195-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7a195-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a195-121">Element</span></span>|<span data-ttu-id="7a195-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a195-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a195-123">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="7a195-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7a195-124">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a195-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a195-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a195-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
