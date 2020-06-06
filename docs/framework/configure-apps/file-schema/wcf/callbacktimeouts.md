---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398192"
---
# \<callbackTimeouts>
<span data-ttu-id="36cae-101">Sunucudan bir çift yönlü geri çağırma sözleşmesi senaryosuna client.in için işlem akışı yaparken zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36cae-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="36cae-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36cae-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="36cae-103">Tür</span><span class="sxs-lookup"><span data-stu-id="36cae-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36cae-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36cae-104">Attributes and Elements</span></span>  
 <span data-ttu-id="36cae-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36cae-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36cae-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36cae-106">Attributes</span></span>  
  
|<span data-ttu-id="36cae-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36cae-107">Attribute</span></span>|<span data-ttu-id="36cae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36cae-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="36cae-109"><xref:System.TimeSpan>İşlemlerin tamamlaması gereken veya otomatik olarak sonlandırılacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="36cae-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="36cae-110">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="36cae-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36cae-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36cae-111">Child Elements</span></span>  
 <span data-ttu-id="36cae-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="36cae-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36cae-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36cae-113">Parent Elements</span></span>  
  
|<span data-ttu-id="36cae-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="36cae-114">Element</span></span>|<span data-ttu-id="36cae-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36cae-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="36cae-116">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="36cae-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36cae-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36cae-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
