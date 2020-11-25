---
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
ms.openlocfilehash: e2903637faa11a3c0a62080cc6fafcf1fc668a56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705000"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="fa45d-102">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="fa45d-102">CorGCReferenceType Enumeration</span></span>

<span data-ttu-id="fa45d-103">Atık olarak toplanmış bir nesnenin kaynağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa45d-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa45d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fa45d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fa45d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa45d-105">Members</span></span>  
  
|<span data-ttu-id="fa45d-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="fa45d-106">Member name</span></span>|<span data-ttu-id="fa45d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa45d-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="fa45d-108">Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.</span><span class="sxs-lookup"><span data-stu-id="fa45d-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="fa45d-109">Nesne tutamacı tablosundan sabitlenmiş güçlü başvuruya yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="fa45d-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="fa45d-110">Nesne tutamacı tablosundan zayıf başvuruya yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="fa45d-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="fa45d-111">Nesne tutamacı tablosundan zayıf başvuru sayılı bir nesne için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="fa45d-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="fa45d-112">Nesne tutamacı tablosundan başvuru sayılı bir nesne için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="fa45d-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="fa45d-113">Nesne tutamacı tablosundan bağımlı nesneye yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="fa45d-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="fa45d-114">Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.</span><span class="sxs-lookup"><span data-stu-id="fa45d-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="fa45d-115">Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.</span><span class="sxs-lookup"><span data-stu-id="fa45d-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="fa45d-116">Yönetilen yığından bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="fa45d-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="fa45d-117">Sonlandırıcı sırasından bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="fa45d-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="fa45d-118">Yalnızca corhandlestrong</span><span class="sxs-lookup"><span data-stu-id="fa45d-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="fa45d-119">Yalnızca tanıtıcı tablosundan güçlü başvurular döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa45d-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="fa45d-120">Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa45d-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="fa45d-121">Tanıtıcı tablosundan yalnızca zayıf başvuruları döndürün.</span><span class="sxs-lookup"><span data-stu-id="fa45d-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="fa45d-122">Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa45d-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="fa45d-123">Tanıtıcı tablosundan tüm başvuruları döndürün.</span><span class="sxs-lookup"><span data-stu-id="fa45d-123">Return all references from the handle table.</span></span> <span data-ttu-id="fa45d-124">Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa45d-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa45d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa45d-125">Remarks</span></span>  

 <span data-ttu-id="fa45d-126">`CorGCReferenceType`Sabit listesi aşağıdaki gibi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="fa45d-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="fa45d-127">`type` [Cor_gc_reference](cor-gc-reference-structure.md) yapısı alanının değeri olarak, bir başvurunun veya tanıtıcının kaynağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa45d-127">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="fa45d-128">`types` [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) metoduna bağımsız değişken olarak, sabit listesine dahil edilecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa45d-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa45d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa45d-129">Requirements</span></span>  

 <span data-ttu-id="fa45d-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa45d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa45d-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fa45d-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa45d-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fa45d-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa45d-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa45d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa45d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa45d-134">See also</span></span>

- [<span data-ttu-id="fa45d-135">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="fa45d-135">Debugging Enumerations</span></span>](debugging-enumerations.md)
