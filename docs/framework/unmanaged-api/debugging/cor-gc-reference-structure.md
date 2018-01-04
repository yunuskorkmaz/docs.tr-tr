---
title: "COR_GC_REFERENCE Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86604febb7641eef147608e564a27883fdc4bec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreference-structure"></a><span data-ttu-id="76f84-102">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="76f84-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="76f84-103">Çöp toplanan olması için bir nesne hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="76f84-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76f84-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="76f84-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="76f84-105">Members</span></span>  
  
|<span data-ttu-id="76f84-106">Üye</span><span class="sxs-lookup"><span data-stu-id="76f84-106">Member</span></span>|<span data-ttu-id="76f84-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76f84-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="76f84-108">Tanıtıcı veya nesne ait olduğu uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76f84-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="76f84-109">Değeri aşağıdakilerden biri olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="76f84-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="76f84-110">Bir Icordebugvalue veya çöpünün toplanma olmasını nesnesine karşılık gelen bir Icordebugreferencevalue arabirimi.</span><span class="sxs-lookup"><span data-stu-id="76f84-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="76f84-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) kök nereden geldiğini belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="76f84-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="76f84-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="76f84-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="76f84-113">Çöp toplanan olmasını nesne hakkında ek veriler.</span><span class="sxs-lookup"><span data-stu-id="76f84-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="76f84-114">Bu bilgiler belirtildiği gibi nesnenin kaynağa bağlıdır `type` alan.</span><span class="sxs-lookup"><span data-stu-id="76f84-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="76f84-115">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="76f84-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76f84-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76f84-116">Remarks</span></span>  
 <span data-ttu-id="76f84-117">`type` Alan bir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) başvuru nereden geldiğini belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="76f84-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="76f84-118">Belirli bir `COR_GC_REFERENCE` değeri herhangi bir yönetilen nesneler şu tür yansıtır:</span><span class="sxs-lookup"><span data-stu-id="76f84-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
-   <span data-ttu-id="76f84-119">Tüm yönetilen yığınları nesnelerden (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="76f84-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="76f84-120">Bu Canlı başvuruları ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra, yönetilen kod içerir.</span><span class="sxs-lookup"><span data-stu-id="76f84-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="76f84-121">Tanıtıcı tablosunu nesnelerden (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="76f84-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="76f84-122">Bu güçlü başvurular içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve bir modüldeki statik değişkenler.</span><span class="sxs-lookup"><span data-stu-id="76f84-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="76f84-123">Sonlandırıcı sıranın nesnelerden (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="76f84-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="76f84-124">Sonlandırıcıyı çalıştırılana dek sonlandırıcıyı sıranın nesneleri kökleri.</span><span class="sxs-lookup"><span data-stu-id="76f84-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="76f84-125">`extraData` Alan başvuru kaynağı (veya türünü) bağlı olarak fazladan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="76f84-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="76f84-126">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="76f84-126">Possible values are:</span></span>  
  
-   <span data-ttu-id="76f84-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="76f84-127">`DependentSource`.</span></span> <span data-ttu-id="76f84-128">Varsa `type` olan `CorGCREferenceType.CorHandleStrongDependent`, bu alan, etkin değilse, atık olarak toplanmış olmasını nesne kökleri nesnedir `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="76f84-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
-   <span data-ttu-id="76f84-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="76f84-129">`RefCount`.</span></span> <span data-ttu-id="76f84-130">Varsa `type` olan `CorGCREferenceType.CorHandleStrongRefCount`, bu alan başvuru tanıtıcısı sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="76f84-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
-   <span data-ttu-id="76f84-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="76f84-131">`Size`.</span></span> <span data-ttu-id="76f84-132">Varsa `type` olan `CorGCREferenceType.CorHandleStrongSizedByref`, bu alan son atık toplayıcı nesnesi kökleri hesaplanan nesne ağacına boyutudur.</span><span class="sxs-lookup"><span data-stu-id="76f84-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="76f84-133">Bu hesaplama mutlaka güncel olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76f84-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f84-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76f84-134">Requirements</span></span>  
 <span data-ttu-id="76f84-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f84-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f84-136">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76f84-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76f84-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76f84-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76f84-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f84-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f84-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76f84-139">See Also</span></span>  
 [<span data-ttu-id="76f84-140">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="76f84-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="76f84-141">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="76f84-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
