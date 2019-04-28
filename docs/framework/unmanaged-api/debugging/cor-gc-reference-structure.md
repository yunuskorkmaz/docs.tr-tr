---
title: COR_GC_REFERENCE Yapısı
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1e31e95473136bf7e7c196eacc278fa8a1caab2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609470"
---
# <a name="corgcreference-structure"></a><span data-ttu-id="90bd7-102">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="90bd7-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="90bd7-103">Atık olarak toplanmış olacak bir nesneyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="90bd7-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90bd7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90bd7-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="90bd7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="90bd7-105">Members</span></span>  
  
|<span data-ttu-id="90bd7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="90bd7-106">Member</span></span>|<span data-ttu-id="90bd7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90bd7-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="90bd7-108">Bir işaretçi tanıtıcı veya nesne ait olduğu uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="90bd7-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="90bd7-109">Değeri aşağıdakilerden biri olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="90bd7-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="90bd7-110">Bir Icordebugvalue veya atık olarak toplanmış olmasını nesnesine karşılık gelen bir Icordebugreferencevalue arabirimi.</span><span class="sxs-lookup"><span data-stu-id="90bd7-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="90bd7-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) kök nereden geldiğini belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="90bd7-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="90bd7-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="90bd7-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="90bd7-113">Atık olarak toplanmış alınacak nesneyi ilgili ek veriler.</span><span class="sxs-lookup"><span data-stu-id="90bd7-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="90bd7-114">Bu bilgileri gösterildiği gibi kaynak nesnenin bağlıdır `type` alan.</span><span class="sxs-lookup"><span data-stu-id="90bd7-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="90bd7-115">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="90bd7-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90bd7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90bd7-116">Remarks</span></span>  
 <span data-ttu-id="90bd7-117">`type` Alan bir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) başvuru nereden geldiğini belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="90bd7-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="90bd7-118">Belirli bir `COR_GC_REFERENCE` değerini herhangi bir yönetilen nesneler aşağıdaki türde yansıtmak:</span><span class="sxs-lookup"><span data-stu-id="90bd7-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="90bd7-119">Tüm yönetilen yığında nesneleri (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="90bd7-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="90bd7-120">Bu, ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra yönetilen kod kullanarak canlı başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="90bd7-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="90bd7-121">Nesne işleyicisi tablosundan (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="90bd7-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="90bd7-122">Bu güçlü atıflar içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve Modül içindeki statik değişkenler.</span><span class="sxs-lookup"><span data-stu-id="90bd7-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="90bd7-123">Sonlandırma sırasından nesneleri (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="90bd7-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="90bd7-124">Sonlandırıcı çalıştırılana dek Sonlandırıcı kuyruğunda nesneleri kökleri.</span><span class="sxs-lookup"><span data-stu-id="90bd7-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="90bd7-125">`extraData` Alanı başvuru kaynağı (veya tür) bağlı olarak ek veri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="90bd7-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="90bd7-126">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="90bd7-126">Possible values are:</span></span>  
  
- <span data-ttu-id="90bd7-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="90bd7-127">`DependentSource`.</span></span> <span data-ttu-id="90bd7-128">Varsa `type` olduğu `CorGCREferenceType.CorHandleStrongDependent`, bu alan, etkin değilse, atık olarak toplanmış alınacak nesneyi kökleri nesnedir `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="90bd7-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="90bd7-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="90bd7-129">`RefCount`.</span></span> <span data-ttu-id="90bd7-130">Varsa `type` olduğu `CorGCREferenceType.CorHandleStrongRefCount`, tanıtıcı başvurusu sayısı bu alandır.</span><span class="sxs-lookup"><span data-stu-id="90bd7-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="90bd7-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="90bd7-131">`Size`.</span></span> <span data-ttu-id="90bd7-132">Varsa `type` olduğu `CorGCREferenceType.CorHandleStrongSizedByref`, bu alan atık toplayıcı nesne kökleri hesaplanan nesne ağacının son boyutudur.</span><span class="sxs-lookup"><span data-stu-id="90bd7-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="90bd7-133">Bu hesaplama mutlaka güncel olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="90bd7-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90bd7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90bd7-134">Requirements</span></span>  
 <span data-ttu-id="90bd7-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90bd7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90bd7-136">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90bd7-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90bd7-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90bd7-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90bd7-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90bd7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90bd7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90bd7-139">See also</span></span>

- [<span data-ttu-id="90bd7-140">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="90bd7-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="90bd7-141">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="90bd7-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
