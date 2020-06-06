---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400071"
---
# \<persistenceProvider>
<span data-ttu-id="8bbc3-101">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="8bbc3-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bbc3-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bbc3-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bbc3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8bbc3-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bbc3-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8bbc3-105">Attributes</span></span>  
  
|<span data-ttu-id="8bbc3-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8bbc3-106">Attribute</span></span>|<span data-ttu-id="8bbc3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bbc3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bbc3-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="8bbc3-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="8bbc3-109"><xref:System.TimeSpan>Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="8bbc3-110">Varsayılan değer "00:00:30" dır.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="8bbc3-111">tür</span><span class="sxs-lookup"><span data-stu-id="8bbc3-111">type</span></span>|<span data-ttu-id="8bbc3-112">Kullanılacak kalıcılık sağlayıcısı fabrikası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bbc3-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bbc3-113">Child Elements</span></span>  
 <span data-ttu-id="8bbc3-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bbc3-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bbc3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8bbc3-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="8bbc3-116">Element</span></span>|<span data-ttu-id="8bbc3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bbc3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8bbc3-118">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bbc3-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bbc3-119">Remarks</span></span>  
 <span data-ttu-id="8bbc3-120">Bu öğe, bir WCF hizmetinin durumunu seri hale getirmek için kullanılacak Kalıcılık sağlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="8bbc3-121">`wsHttpContextBinding`Http üst bilgilerinde durum bilgilerini geçiren ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bbc3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bbc3-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
