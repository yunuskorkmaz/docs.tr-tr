---
description: 'Hakkında daha fazla bilgi edinin: <persistenceProvider>'
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 60ddaf9f26f496bd7d79ccab84f84135e46963d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683560"
---
# \<persistenceProvider>

<span data-ttu-id="59848-102">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59848-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="59848-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="59848-103">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59848-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59848-104">Attributes and Elements</span></span>  

 <span data-ttu-id="59848-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59848-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59848-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59848-106">Attributes</span></span>  
  
|<span data-ttu-id="59848-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59848-107">Attribute</span></span>|<span data-ttu-id="59848-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59848-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59848-109">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="59848-109">persistenceOperationTimeout</span></span>|<span data-ttu-id="59848-110"><xref:System.TimeSpan>Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="59848-110">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="59848-111">Varsayılan değer "00:00:30" dır.</span><span class="sxs-lookup"><span data-stu-id="59848-111">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="59848-112">tür</span><span class="sxs-lookup"><span data-stu-id="59848-112">type</span></span>|<span data-ttu-id="59848-113">Kullanılacak kalıcılık sağlayıcısı fabrikası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="59848-113">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59848-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59848-114">Child Elements</span></span>  

 <span data-ttu-id="59848-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="59848-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59848-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59848-116">Parent Elements</span></span>  
  
|<span data-ttu-id="59848-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="59848-117">Element</span></span>|<span data-ttu-id="59848-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59848-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="59848-119">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="59848-119">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59848-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59848-120">Remarks</span></span>  

 <span data-ttu-id="59848-121">Bu öğe, bir WCF hizmetinin durumunu seri hale getirmek için kullanılacak Kalıcılık sağlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59848-121">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="59848-122">`wsHttpContextBinding`Http üst bilgilerinde durum bilgilerini geçiren ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59848-122">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59848-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59848-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
