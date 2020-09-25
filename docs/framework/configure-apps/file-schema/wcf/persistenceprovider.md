---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dbf0ba565d4e3e2d65b4a81eb5d345fa90fb43c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181433"
---
# \<persistenceProvider>

<span data-ttu-id="bb4d8-101">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="bb4d8-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="bb4d8-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb4d8-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb4d8-103">Attributes and Elements</span></span>  

 <span data-ttu-id="bb4d8-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb4d8-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb4d8-105">Attributes</span></span>  
  
|<span data-ttu-id="bb4d8-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bb4d8-106">Attribute</span></span>|<span data-ttu-id="bb4d8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb4d8-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb4d8-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="bb4d8-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="bb4d8-109"><xref:System.TimeSpan>Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="bb4d8-110">Varsayılan değer "00:00:30" dır.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="bb4d8-111">tür</span><span class="sxs-lookup"><span data-stu-id="bb4d8-111">type</span></span>|<span data-ttu-id="bb4d8-112">Kullanılacak kalıcılık sağlayıcısı fabrikası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb4d8-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb4d8-113">Child Elements</span></span>  

 <span data-ttu-id="bb4d8-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb4d8-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb4d8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bb4d8-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb4d8-116">Element</span></span>|<span data-ttu-id="bb4d8-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb4d8-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bb4d8-118">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb4d8-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb4d8-119">Remarks</span></span>  

 <span data-ttu-id="bb4d8-120">Bu öğe, bir WCF hizmetinin durumunu seri hale getirmek için kullanılacak Kalıcılık sağlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="bb4d8-121">`wsHttpContextBinding`Http üst bilgilerinde durum bilgilerini geçiren ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb4d8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb4d8-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
