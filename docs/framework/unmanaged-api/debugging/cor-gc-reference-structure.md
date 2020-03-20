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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179326"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="db127-102">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="db127-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="db127-103">Çöp toplanacak bir nesne hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="db127-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db127-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db127-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="db127-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="db127-105">Members</span></span>  
  
|<span data-ttu-id="db127-106">Üye</span><span class="sxs-lookup"><span data-stu-id="db127-106">Member</span></span>|<span data-ttu-id="db127-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db127-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="db127-108">Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db127-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="db127-109">Değeri. `null`</span><span class="sxs-lookup"><span data-stu-id="db127-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="db127-110">Çöp toplanacak nesneye karşılık gelen bir ICorDebugValue veya ICorDebugReferenceValue arabirimi.</span><span class="sxs-lookup"><span data-stu-id="db127-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="db127-111">Kökün nereden geldiğini gösteren [bir CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="db127-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="db127-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="db127-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="db127-113">Çöp toplanacak nesne yle ilgili ek veriler.</span><span class="sxs-lookup"><span data-stu-id="db127-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="db127-114">Bu bilgiler, alan tarafından belirtildiği gibi nesnenin `type` kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="db127-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="db127-115">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="db127-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db127-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db127-116">Remarks</span></span>  
 <span data-ttu-id="db127-117">Alan, `type` başvurunun nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeridir.</span><span class="sxs-lookup"><span data-stu-id="db127-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="db127-118">Belirli `COR_GC_REFERENCE` bir değer, aşağıdaki yönetilen nesnelerden herhangi birini yansıtabilir:</span><span class="sxs-lookup"><span data-stu-id="db127-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="db127-119">Yönetilen tüm yığınlardan nesneler`CorGCReferenceType.CorReferenceStack`( ).</span><span class="sxs-lookup"><span data-stu-id="db127-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="db127-120">Bu, yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="db127-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="db127-121">Tutamaç tablosundaki nesneler`CorGCReferenceType.CorHandle*`( ).</span><span class="sxs-lookup"><span data-stu-id="db127-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="db127-122">Bu, bir`HNDTYPE_STRONG` modüldeki güçlü başvuruları ( ve ) ve `HNDTYPE_REFCOUNT`statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="db127-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="db127-123">Sonlandırıcı sıradaki nesneler (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="db127-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="db127-124">Sonlandırıcı sıra, sonlandırıcı çalışana kadar nesneleri kökler.</span><span class="sxs-lookup"><span data-stu-id="db127-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="db127-125">Alan, `extraData` başvurunun kaynağına (veya türüne) bağlı olarak ek veri içerir.</span><span class="sxs-lookup"><span data-stu-id="db127-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="db127-126">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="db127-126">Possible values are:</span></span>  
  
- <span data-ttu-id="db127-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="db127-127">`DependentSource`.</span></span> <span data-ttu-id="db127-128">`type` Ise `CorGCREferenceType.CorHandleStrongDependent`, bu alan nesne ise, eğer canlı, kökler nesne çöp `COR_GC_REFERENCE.Location`toplanan.</span><span class="sxs-lookup"><span data-stu-id="db127-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="db127-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="db127-129">`RefCount`.</span></span> <span data-ttu-id="db127-130">`type` Ise `CorGCREferenceType.CorHandleStrongRefCount`, bu alan tanıtıcının başvuru sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="db127-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="db127-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="db127-131">`Size`.</span></span> <span data-ttu-id="db127-132">`type` Ise `CorGCREferenceType.CorHandleStrongSizedByref`, bu alan, çöp toplayıcınesne kökleri hesaplanan nesne ağacının son boyutudur.</span><span class="sxs-lookup"><span data-stu-id="db127-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="db127-133">Bu hesaplamanın güncel olmaması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="db127-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db127-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db127-134">Requirements</span></span>  
 <span data-ttu-id="db127-135">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db127-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db127-136">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db127-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db127-137">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db127-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db127-138">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db127-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db127-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db127-139">See also</span></span>

- [<span data-ttu-id="db127-140">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="db127-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="db127-141">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="db127-141">Debugging</span></span>](index.md)
