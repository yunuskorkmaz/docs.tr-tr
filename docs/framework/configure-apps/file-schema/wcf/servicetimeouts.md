---
description: 'Hakkında daha fazla bilgi edinin: <serviceTimeouts>'
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: bc9ef99078f8c6fa3b441604e14df928eec054e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682734"
---
# \<serviceTimeouts>

<span data-ttu-id="50d23-102">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="50d23-102">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="50d23-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="50d23-103">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="50d23-104">Tür</span><span class="sxs-lookup"><span data-stu-id="50d23-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50d23-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="50d23-105">Attributes and Elements</span></span>  

 <span data-ttu-id="50d23-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50d23-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50d23-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50d23-107">Attributes</span></span>  
  
|<span data-ttu-id="50d23-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50d23-108">Attribute</span></span>|<span data-ttu-id="50d23-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50d23-109">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="50d23-110"><xref:System.TimeSpan>Bir işlemin istemciden sunucuya akışı gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="50d23-110">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="50d23-111">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="50d23-111">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50d23-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="50d23-112">Child Elements</span></span>  

 <span data-ttu-id="50d23-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="50d23-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50d23-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="50d23-114">Parent Elements</span></span>  
  
|<span data-ttu-id="50d23-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="50d23-115">Element</span></span>|<span data-ttu-id="50d23-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50d23-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="50d23-117">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="50d23-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50d23-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50d23-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
