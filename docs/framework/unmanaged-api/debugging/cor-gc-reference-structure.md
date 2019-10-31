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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099136"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="23e18-102">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="23e18-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="23e18-103">Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="23e18-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23e18-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="23e18-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="23e18-105">Members</span></span>  
  
|<span data-ttu-id="23e18-106">Üye</span><span class="sxs-lookup"><span data-stu-id="23e18-106">Member</span></span>|<span data-ttu-id="23e18-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23e18-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="23e18-108">Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="23e18-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="23e18-109">Değeri `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="23e18-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="23e18-110">Atık toplanan nesneye karşılık gelen bir ICorDebugValue ya da ICorDebugReferenceValue arabirimi.</span><span class="sxs-lookup"><span data-stu-id="23e18-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="23e18-111">Kökün nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="23e18-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="23e18-112">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="23e18-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="23e18-113">Atık olarak toplanmış nesne hakkında ek veriler.</span><span class="sxs-lookup"><span data-stu-id="23e18-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="23e18-114">Bu bilgiler, `type` alanı tarafından belirtilen şekilde nesnenin kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="23e18-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="23e18-115">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="23e18-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23e18-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23e18-116">Remarks</span></span>  
 <span data-ttu-id="23e18-117">`type` alanı, başvurunun nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeridir.</span><span class="sxs-lookup"><span data-stu-id="23e18-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="23e18-118">Belirli bir `COR_GC_REFERENCE` değeri aşağıdaki yönetilen nesne türlerinden herhangi birini yansıtabilir:</span><span class="sxs-lookup"><span data-stu-id="23e18-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="23e18-119">Tüm yönetilen yığınlardan nesneler (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="23e18-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="23e18-120">Bu, Yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="23e18-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="23e18-121">Tanıtıcı tablosundan nesneler (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="23e18-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="23e18-122">Bu, bir modülde tanımlayıcı başvuruları (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="23e18-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="23e18-123">Sonlandırıcı kuyruğundan nesneler (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="23e18-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="23e18-124">Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.</span><span class="sxs-lookup"><span data-stu-id="23e18-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="23e18-125">`extraData` alan, başvurunun kaynağına (veya türüne) bağlı olarak ek veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="23e18-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="23e18-126">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="23e18-126">Possible values are:</span></span>  
  
- <span data-ttu-id="23e18-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="23e18-127">`DependentSource`.</span></span> <span data-ttu-id="23e18-128">`type` `CorGCREferenceType.CorHandleStrongDependent`ise, bu alan, etkin olduğunda, nesneyi `COR_GC_REFERENCE.Location`atık olarak toplanabilecek şekilde Kökbir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="23e18-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="23e18-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="23e18-129">`RefCount`.</span></span> <span data-ttu-id="23e18-130">`type` `CorGCREferenceType.CorHandleStrongRefCount`ise, bu alan tanıtıcının başvuru sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="23e18-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="23e18-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="23e18-131">`Size`.</span></span> <span data-ttu-id="23e18-132">`type` `CorGCREferenceType.CorHandleStrongSizedByref`ise, bu alan çöp toplayıcının nesne köklerinin hesaplandığı nesne ağacının son boyutudur.</span><span class="sxs-lookup"><span data-stu-id="23e18-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="23e18-133">Bu hesaplamanın güncel olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="23e18-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23e18-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23e18-134">Requirements</span></span>  
 <span data-ttu-id="23e18-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23e18-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23e18-136">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23e18-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23e18-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="23e18-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23e18-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23e18-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e18-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23e18-139">See also</span></span>

- [<span data-ttu-id="23e18-140">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="23e18-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="23e18-141">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="23e18-141">Debugging</span></span>](index.md)
