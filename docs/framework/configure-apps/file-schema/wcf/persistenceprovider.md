---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: ba02977a7df44931ae195040949e9a8eb0c141b5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152027"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="7df9b-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="7df9b-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="7df9b-103">Kullanılacak Kalıcılık sağlayıcı uygulanması yanı sıra Kalıcılık işlemleri için kullanılacak zaman aşımını türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7df9b-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="7df9b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7df9b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7df9b-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="7df9b-105">\<behaviors></span></span>  
<span data-ttu-id="7df9b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7df9b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7df9b-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7df9b-107">\<behavior></span></span>  
<span data-ttu-id="7df9b-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="7df9b-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df9b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7df9b-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7df9b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7df9b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7df9b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7df9b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7df9b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7df9b-112">Attributes</span></span>  
  
|<span data-ttu-id="7df9b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7df9b-113">Attribute</span></span>|<span data-ttu-id="7df9b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df9b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7df9b-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="7df9b-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="7df9b-116">A <xref:System.TimeSpan> Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7df9b-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="7df9b-117">Varsayılan değer "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="7df9b-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="7df9b-118">türü</span><span class="sxs-lookup"><span data-stu-id="7df9b-118">type</span></span>|<span data-ttu-id="7df9b-119">Kullanılacak Kalıcılık sağlayıcı üreteci türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7df9b-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7df9b-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7df9b-120">Child Elements</span></span>  
 <span data-ttu-id="7df9b-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="7df9b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7df9b-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7df9b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7df9b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="7df9b-123">Element</span></span>|<span data-ttu-id="7df9b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df9b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7df9b-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7df9b-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7df9b-126">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7df9b-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7df9b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7df9b-127">Remarks</span></span>  
 <span data-ttu-id="7df9b-128">Bu öğe bir WCF Hizmeti durumunu serileştirmek için kullanılacak Kalıcılık sağlayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7df9b-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="7df9b-129">İle birlikte kullanılmalıdır `wsHttpContextBinding` HTTP üst bilgilerinde durum bilgilerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="7df9b-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df9b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7df9b-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
