---
description: 'Hakkında daha fazla bilgi edinin: CorGCReferenceType numaralandırması'
title: CorGCReferenceType Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: a1f534f9fe4b9ba4ede0bef94f35cf1688fe1817
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801520"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="7bb82-103">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7bb82-103">CorGCReferenceType Enumeration</span></span>

<span data-ttu-id="7bb82-104">Atık olarak toplanmış bir nesnenin kaynağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bb82-104">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb82-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7bb82-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="7bb82-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7bb82-106">Members</span></span>  
  
|<span data-ttu-id="7bb82-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="7bb82-107">Member name</span></span>|<span data-ttu-id="7bb82-108">Description</span><span class="sxs-lookup"><span data-stu-id="7bb82-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="7bb82-109">Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.</span><span class="sxs-lookup"><span data-stu-id="7bb82-109">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="7bb82-110">Nesne tutamacı tablosundan sabitlenmiş güçlü başvuruya yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb82-110">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="7bb82-111">Nesne tutamacı tablosundan zayıf başvuruya yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb82-111">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="7bb82-112">Nesne tutamacı tablosundan zayıf başvuru sayılı bir nesne için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb82-112">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="7bb82-113">Nesne tutamacı tablosundan başvuru sayılı bir nesne için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb82-113">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="7bb82-114">Nesne tutamacı tablosundan bağımlı nesneye yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb82-114">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="7bb82-115">Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.</span><span class="sxs-lookup"><span data-stu-id="7bb82-115">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="7bb82-116">Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.</span><span class="sxs-lookup"><span data-stu-id="7bb82-116">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="7bb82-117">Yönetilen yığından bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="7bb82-117">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="7bb82-118">Sonlandırıcı sırasından bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="7bb82-118">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="7bb82-119">Yalnızca corhandlestrong</span><span class="sxs-lookup"><span data-stu-id="7bb82-119">CorHandleStrongOnly</span></span>|<span data-ttu-id="7bb82-120">Yalnızca tanıtıcı tablosundan güçlü başvurular döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bb82-120">Return only strong references from the handle table.</span></span> <span data-ttu-id="7bb82-121">Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bb82-121">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="7bb82-122">Tanıtıcı tablosundan yalnızca zayıf başvuruları döndürün.</span><span class="sxs-lookup"><span data-stu-id="7bb82-122">Return only weak references from the handle table.</span></span> <span data-ttu-id="7bb82-123">Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bb82-123">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="7bb82-124">Tanıtıcı tablosundan tüm başvuruları döndürün.</span><span class="sxs-lookup"><span data-stu-id="7bb82-124">Return all references from the handle table.</span></span> <span data-ttu-id="7bb82-125">Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bb82-125">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb82-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bb82-126">Remarks</span></span>  

 <span data-ttu-id="7bb82-127">`CorGCReferenceType`Sabit listesi aşağıdaki gibi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7bb82-127">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="7bb82-128">`type` [Cor_gc_reference](cor-gc-reference-structure.md) yapısı alanının değeri olarak, bir başvurunun veya tanıtıcının kaynağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bb82-128">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="7bb82-129">`types` [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) metoduna bağımsız değişken olarak, sabit listesine dahil edilecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bb82-129">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb82-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bb82-130">Requirements</span></span>  

 <span data-ttu-id="7bb82-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb82-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb82-132">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7bb82-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bb82-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7bb82-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bb82-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb82-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb82-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb82-135">See also</span></span>

- [<span data-ttu-id="7bb82-136">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7bb82-136">Debugging Enumerations</span></span>](debugging-enumerations.md)
