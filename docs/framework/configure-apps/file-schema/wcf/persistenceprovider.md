---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 8deca5b4bec4808ac9add201db0c936764fddcb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602227"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="4b00e-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="4b00e-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="4b00e-103">Kullanılacak Kalıcılık sağlayıcı uygulanması yanı sıra Kalıcılık işlemleri için kullanılacak zaman aşımını türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b00e-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="4b00e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b00e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b00e-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4b00e-105">\<behaviors></span></span>  
<span data-ttu-id="4b00e-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4b00e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4b00e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4b00e-107">\<behavior></span></span>  
<span data-ttu-id="4b00e-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="4b00e-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b00e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b00e-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b00e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b00e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4b00e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b00e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b00e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b00e-112">Attributes</span></span>  
  
|<span data-ttu-id="4b00e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b00e-113">Attribute</span></span>|<span data-ttu-id="4b00e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b00e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b00e-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="4b00e-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="4b00e-116">A <xref:System.TimeSpan> Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4b00e-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="4b00e-117">Varsayılan değer "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="4b00e-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="4b00e-118">türü</span><span class="sxs-lookup"><span data-stu-id="4b00e-118">type</span></span>|<span data-ttu-id="4b00e-119">Kullanılacak Kalıcılık sağlayıcı üreteci türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4b00e-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b00e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b00e-120">Child Elements</span></span>  
 <span data-ttu-id="4b00e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b00e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b00e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b00e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4b00e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b00e-123">Element</span></span>|<span data-ttu-id="4b00e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b00e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b00e-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4b00e-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4b00e-126">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b00e-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b00e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b00e-127">Remarks</span></span>  
 <span data-ttu-id="4b00e-128">Bu öğe bir WCF Hizmeti durumunu serileştirmek için kullanılacak Kalıcılık sağlayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b00e-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="4b00e-129">İle birlikte kullanılmalıdır `wsHttpContextBinding` HTTP üst bilgilerinde durum bilgilerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="4b00e-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b00e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b00e-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
