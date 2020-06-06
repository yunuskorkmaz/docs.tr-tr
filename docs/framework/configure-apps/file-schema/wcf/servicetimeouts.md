---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399557"
---
# \<serviceTimeouts>
<span data-ttu-id="048d4-101">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="048d4-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="048d4-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="048d4-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="048d4-103">Tür</span><span class="sxs-lookup"><span data-stu-id="048d4-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="048d4-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="048d4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="048d4-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="048d4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="048d4-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="048d4-106">Attributes</span></span>  
  
|<span data-ttu-id="048d4-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="048d4-107">Attribute</span></span>|<span data-ttu-id="048d4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="048d4-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="048d4-109"><xref:System.TimeSpan>Bir işlemin istemciden sunucuya akışı gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="048d4-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="048d4-110">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="048d4-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="048d4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="048d4-111">Child Elements</span></span>  
 <span data-ttu-id="048d4-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="048d4-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="048d4-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="048d4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="048d4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="048d4-114">Element</span></span>|<span data-ttu-id="048d4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="048d4-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="048d4-116">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="048d4-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="048d4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="048d4-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
