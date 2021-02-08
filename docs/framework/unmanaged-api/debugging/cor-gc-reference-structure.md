---
description: 'Daha fazla bilgi edinin: COR_GC_REFERENCE yapısı'
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
ms.openlocfilehash: 38518bb1eb870081621bf32af9e63cdaa208dbd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801819"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="f1308-103">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="f1308-103">COR_GC_REFERENCE Structure</span></span>

<span data-ttu-id="f1308-104">Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1308-104">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1308-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1308-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="f1308-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f1308-106">Members</span></span>  
  
|<span data-ttu-id="f1308-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f1308-107">Member</span></span>|<span data-ttu-id="f1308-108">Description</span><span class="sxs-lookup"><span data-stu-id="f1308-108">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="f1308-109">Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1308-109">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="f1308-110">Değeri olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="f1308-110">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="f1308-111">Atık toplanan nesneye karşılık gelen bir ICorDebugValue ya da ICorDebugReferenceValue arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f1308-111">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="f1308-112">Kökün nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="f1308-112">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="f1308-113">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f1308-113">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="f1308-114">Atık olarak toplanmış nesne hakkında ek veriler.</span><span class="sxs-lookup"><span data-stu-id="f1308-114">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="f1308-115">Bu bilgiler, alanı tarafından belirtildiği gibi nesnenin kaynağına bağlıdır `type` .</span><span class="sxs-lookup"><span data-stu-id="f1308-115">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="f1308-116">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f1308-116">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1308-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1308-117">Remarks</span></span>  

 <span data-ttu-id="f1308-118">`type`Alan, başvurunun nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1308-118">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="f1308-119">Belirli bir `COR_GC_REFERENCE` değer, aşağıdaki yönetilen nesne türlerinden herhangi birini yansıtabilir:</span><span class="sxs-lookup"><span data-stu-id="f1308-119">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="f1308-120">Tüm yönetilen yığınlardaki ( `CorGCReferenceType.CorReferenceStack` ) nesneler.</span><span class="sxs-lookup"><span data-stu-id="f1308-120">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="f1308-121">Bu, Yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1308-121">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="f1308-122">Tanıtıcı tablosundan nesneler ( `CorGCReferenceType.CorHandle*` ).</span><span class="sxs-lookup"><span data-stu-id="f1308-122">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="f1308-123">Bu, bir modüldeki tanımlayıcı başvuruları ( `HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT` ) ve statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1308-123">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="f1308-124">Sonlandırıcı kuyruğundan nesneler ( `CorGCReferenceType.CorReferenceFinalizer` ).</span><span class="sxs-lookup"><span data-stu-id="f1308-124">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="f1308-125">Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.</span><span class="sxs-lookup"><span data-stu-id="f1308-125">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="f1308-126">Bu `extraData` alan, başvurunun kaynağına (veya türüne) bağlı olarak ek veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="f1308-126">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="f1308-127">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f1308-127">Possible values are:</span></span>  
  
- <span data-ttu-id="f1308-128">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="f1308-128">`DependentSource`.</span></span> <span data-ttu-id="f1308-129">Eğer ise `type` `CorGCREferenceType.CorHandleStrongDependent` , bu alan, etkin ise, nesne üzerinde çöp toplanabilecek nesneyi köklendirilir `COR_GC_REFERENCE.Location` .</span><span class="sxs-lookup"><span data-stu-id="f1308-129">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="f1308-130">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="f1308-130">`RefCount`.</span></span> <span data-ttu-id="f1308-131">İse, `type` `CorGCREferenceType.CorHandleStrongRefCount` Bu alan tanıtıcının başvuru sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="f1308-131">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="f1308-132">`Size`.</span><span class="sxs-lookup"><span data-stu-id="f1308-132">`Size`.</span></span> <span data-ttu-id="f1308-133">`type`İse `CorGCREferenceType.CorHandleStrongSizedByref` , bu alan çöp toplayıcının nesne köklerinin hesaplandığı nesne ağacının son boyutudur.</span><span class="sxs-lookup"><span data-stu-id="f1308-133">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="f1308-134">Bu hesaplamanın güncel olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f1308-134">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1308-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1308-135">Requirements</span></span>  

 <span data-ttu-id="f1308-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1308-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1308-137">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1308-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1308-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1308-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1308-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1308-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1308-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1308-140">See also</span></span>

- [<span data-ttu-id="f1308-141">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="f1308-141">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f1308-142">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f1308-142">Debugging</span></span>](index.md)
