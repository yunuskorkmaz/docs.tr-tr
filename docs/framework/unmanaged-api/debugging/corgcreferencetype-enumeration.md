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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a673c98b11fbca5f66e9e1ae61f224448c20797
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207155"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="50782-102">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="50782-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="50782-103">Kaynağı olarak atık olarak toplanmış bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50782-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50782-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50782-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="50782-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="50782-105">Members</span></span>  
  
|<span data-ttu-id="50782-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="50782-106">Member name</span></span>|<span data-ttu-id="50782-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50782-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="50782-108">Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.</span><span class="sxs-lookup"><span data-stu-id="50782-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="50782-109">Nesne işleyicisi tablosundan bir sabitlenmiş güçlü başvuru işleyici.</span><span class="sxs-lookup"><span data-stu-id="50782-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="50782-110">Nesne işleyicisi tablosundan bir tanıtıcı zayıf bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="50782-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="50782-111">Nesne işleyicisi tablosundan bir tanıtıcı zayıf bir başvuru sayılan nesne.</span><span class="sxs-lookup"><span data-stu-id="50782-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="50782-112">Nesne işleyicisi tablosundan bir başvurusu sayılan nesne için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="50782-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="50782-113">Nesne işleyicisi tablosundan bir bağımlı nesne için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="50782-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="50782-114">Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.</span><span class="sxs-lookup"><span data-stu-id="50782-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="50782-115">Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.</span><span class="sxs-lookup"><span data-stu-id="50782-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="50782-116">Yönetilen yığından başvuru.</span><span class="sxs-lookup"><span data-stu-id="50782-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="50782-117">Sonlandırma sırasından bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="50782-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="50782-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="50782-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="50782-119">Yalnızca tanımlayıcı başvuruları, işleyici bir tablo döndürür.</span><span class="sxs-lookup"><span data-stu-id="50782-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="50782-120">Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50782-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="50782-121">Zayıf başvurular yalnızca tanıtıcı bir tablo döndürür.</span><span class="sxs-lookup"><span data-stu-id="50782-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="50782-122">Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50782-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="50782-123">Tüm başvuruları, işleyici bir tablo döndürür.</span><span class="sxs-lookup"><span data-stu-id="50782-123">Return all references from the handle table.</span></span> <span data-ttu-id="50782-124">Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50782-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50782-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50782-125">Remarks</span></span>  
 <span data-ttu-id="50782-126">`CorGCReferenceType` Numaralandırması şu şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="50782-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="50782-127">Değeri olarak `type` alanını [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) yapısı, başvuru veya tanıtıcısı kaynağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50782-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="50782-128">Olarak `types` bağımsız değişkeni [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yöntemi numaralandırmada içerecek şekilde tanıtıcıları türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="50782-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50782-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50782-129">Requirements</span></span>  
 <span data-ttu-id="50782-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50782-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50782-131">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50782-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50782-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50782-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50782-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50782-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50782-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50782-134">See also</span></span>

- [<span data-ttu-id="50782-135">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="50782-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
