---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 98523489aacebf910bcf5d81c479819183887dff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198892"
---
# \<callbackTimeouts>

<span data-ttu-id="50dcf-101">Sunucudan bir çift yönlü geri çağırma sözleşmesi senaryosuna client.in için işlem akışı yaparken zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="50dcf-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="50dcf-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="50dcf-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="50dcf-103">Tür</span><span class="sxs-lookup"><span data-stu-id="50dcf-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50dcf-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="50dcf-104">Attributes and Elements</span></span>  

 <span data-ttu-id="50dcf-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50dcf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50dcf-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50dcf-106">Attributes</span></span>  
  
|<span data-ttu-id="50dcf-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50dcf-107">Attribute</span></span>|<span data-ttu-id="50dcf-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50dcf-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="50dcf-109"><xref:System.TimeSpan>İşlemlerin tamamlaması gereken veya otomatik olarak sonlandırılacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="50dcf-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="50dcf-110">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="50dcf-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50dcf-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="50dcf-111">Child Elements</span></span>  

 <span data-ttu-id="50dcf-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="50dcf-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50dcf-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="50dcf-113">Parent Elements</span></span>  
  
|<span data-ttu-id="50dcf-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="50dcf-114">Element</span></span>|<span data-ttu-id="50dcf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50dcf-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="50dcf-116">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="50dcf-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50dcf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50dcf-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
