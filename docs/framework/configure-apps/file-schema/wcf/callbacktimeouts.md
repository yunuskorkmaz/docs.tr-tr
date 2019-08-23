---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: d57a888a19e684ac13632c1ab2476e304667c3e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919660"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="8a553-101">\<Callbackzamanaşımları ></span><span class="sxs-lookup"><span data-stu-id="8a553-101">\<callbackTimeouts></span></span>
<span data-ttu-id="8a553-102">Sunucudan bir çift yönlü geri çağırma sözleşmesi senaryosuna client.in için işlem akışı yaparken zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a553-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="8a553-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8a553-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8a553-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8a553-104">\<behaviors></span></span>  
<span data-ttu-id="8a553-105">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="8a553-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="8a553-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8a553-106">\<behavior></span></span>  
<span data-ttu-id="8a553-107">\<Callbackzamanaşımları ></span><span class="sxs-lookup"><span data-stu-id="8a553-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a553-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a553-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="8a553-109">Tür</span><span class="sxs-lookup"><span data-stu-id="8a553-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a553-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a553-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8a553-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a553-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a553-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8a553-112">Attributes</span></span>  
  
|<span data-ttu-id="8a553-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8a553-113">Attribute</span></span>|<span data-ttu-id="8a553-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a553-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="8a553-115">İşlemlerin <xref:System.TimeSpan> tamamlaması gereken veya otomatik olarak sonlandırılacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8a553-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="8a553-116">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="8a553-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a553-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a553-117">Child Elements</span></span>  
 <span data-ttu-id="8a553-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a553-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a553-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a553-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8a553-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a553-120">Element</span></span>|<span data-ttu-id="8a553-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a553-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a553-122">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8a553-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8a553-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a553-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a553-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a553-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
