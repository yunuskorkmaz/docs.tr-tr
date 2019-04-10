---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dc8dea0ddd1ea074c08952e3e2ebfef2d12f7183
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099293"
---
# <a name="persistenceprovider"></a><span data-ttu-id="d51e6-101">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="d51e6-101">\<persistenceProvider></span></span>
<span data-ttu-id="d51e6-102">Kullanılacak Kalıcılık sağlayıcı uygulanması yanı sıra Kalıcılık işlemleri için kullanılacak zaman aşımını türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d51e6-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="d51e6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d51e6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d51e6-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d51e6-104">\<behaviors></span></span>  
<span data-ttu-id="d51e6-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d51e6-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="d51e6-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d51e6-106">\<behavior></span></span>  
<span data-ttu-id="d51e6-107">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="d51e6-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51e6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d51e6-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d51e6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d51e6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d51e6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d51e6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d51e6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51e6-111">Attributes</span></span>  
  
|<span data-ttu-id="d51e6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d51e6-112">Attribute</span></span>|<span data-ttu-id="d51e6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51e6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d51e6-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="d51e6-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="d51e6-115">A <xref:System.TimeSpan> Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d51e6-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="d51e6-116">Varsayılan değer "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="d51e6-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="d51e6-117"> türü</span><span class="sxs-lookup"><span data-stu-id="d51e6-117">type</span></span>|<span data-ttu-id="d51e6-118">Kullanılacak Kalıcılık sağlayıcı üreteci türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d51e6-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d51e6-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d51e6-119">Child Elements</span></span>  
 <span data-ttu-id="d51e6-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="d51e6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d51e6-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d51e6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d51e6-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="d51e6-122">Element</span></span>|<span data-ttu-id="d51e6-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51e6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d51e6-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d51e6-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d51e6-125">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d51e6-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d51e6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d51e6-126">Remarks</span></span>  
 <span data-ttu-id="d51e6-127">Bu öğe bir WCF Hizmeti durumunu serileştirmek için kullanılacak Kalıcılık sağlayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d51e6-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="d51e6-128">İle birlikte kullanılmalıdır `wsHttpContextBinding` HTTP üst bilgilerinde durum bilgilerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="d51e6-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51e6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d51e6-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
