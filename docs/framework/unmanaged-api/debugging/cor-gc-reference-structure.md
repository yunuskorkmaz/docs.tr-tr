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
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274232"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="0cabf-102">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="0cabf-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="0cabf-103">Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0cabf-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cabf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cabf-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="0cabf-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0cabf-105">Members</span></span>  
  
|<span data-ttu-id="0cabf-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0cabf-106">Member</span></span>|<span data-ttu-id="0cabf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cabf-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="0cabf-108">Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cabf-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="0cabf-109">Değeri `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cabf-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="0cabf-110">Atık toplanan nesneye karşılık gelen bir ICorDebugValue ya da ICorDebugReferenceValue arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0cabf-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="0cabf-111">Kökün nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="0cabf-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="0cabf-112">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0cabf-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="0cabf-113">Atık olarak toplanmış nesne hakkında ek veriler.</span><span class="sxs-lookup"><span data-stu-id="0cabf-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="0cabf-114">Bu bilgiler, `type` alanı tarafından belirtildiği gibi nesnenin kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cabf-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="0cabf-115">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0cabf-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cabf-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cabf-116">Remarks</span></span>  
 <span data-ttu-id="0cabf-117">Alan, başvurunun nereden geldiğini gösteren bir CorGCReferenceType numaralandırma değeridir. [](corgcreferencetype-enumeration.md) `type`</span><span class="sxs-lookup"><span data-stu-id="0cabf-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="0cabf-118">Belirli `COR_GC_REFERENCE` bir değer, aşağıdaki yönetilen nesne türlerinden herhangi birini yansıtabilir:</span><span class="sxs-lookup"><span data-stu-id="0cabf-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="0cabf-119">Tüm yönetilen yığınlardaki (`CorGCReferenceType.CorReferenceStack`) nesneler.</span><span class="sxs-lookup"><span data-stu-id="0cabf-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="0cabf-120">Bu, Yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0cabf-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="0cabf-121">Tanıtıcı tablosundan nesneler (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="0cabf-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="0cabf-122">Bu, bir modüldeki tanımlayıcı`HNDTYPE_STRONG` başvuruları `HNDTYPE_REFCOUNT`(ve) ve statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0cabf-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="0cabf-123">Sonlandırıcı kuyruğundan nesneler (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="0cabf-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="0cabf-124">Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.</span><span class="sxs-lookup"><span data-stu-id="0cabf-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="0cabf-125">Bu `extraData` alan, başvurunun kaynağına (veya türüne) bağlı olarak ek veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="0cabf-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="0cabf-126">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0cabf-126">Possible values are:</span></span>  
  
- <span data-ttu-id="0cabf-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="0cabf-127">`DependentSource`.</span></span> <span data-ttu-id="0cabf-128">Eğer ise, bu alan, etkin ise, nesne üzerinde `COR_GC_REFERENCE.Location`çöp toplanabilecek nesneyi köklendirilir. `CorGCREferenceType.CorHandleStrongDependent` `type`</span><span class="sxs-lookup"><span data-stu-id="0cabf-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="0cabf-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="0cabf-129">`RefCount`.</span></span> <span data-ttu-id="0cabf-130">`type` İse`CorGCREferenceType.CorHandleStrongRefCount`, bu alan tanıtıcının başvuru sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="0cabf-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="0cabf-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="0cabf-131">`Size`.</span></span> <span data-ttu-id="0cabf-132">`type` İse`CorGCREferenceType.CorHandleStrongSizedByref`, bu alan çöp toplayıcının nesne köklerinin hesaplandığı nesne ağacının son boyutudur.</span><span class="sxs-lookup"><span data-stu-id="0cabf-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="0cabf-133">Bu hesaplamanın güncel olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0cabf-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cabf-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cabf-134">Requirements</span></span>  
 <span data-ttu-id="0cabf-135">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cabf-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cabf-136">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0cabf-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cabf-137">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0cabf-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cabf-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cabf-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cabf-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cabf-139">See also</span></span>

- [<span data-ttu-id="0cabf-140">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="0cabf-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0cabf-141">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0cabf-141">Debugging</span></span>](index.md)
