---
description: 'Daha fazla bilgi edinin: COR_HEAPOBJECT Yapısı'
title: COR_HEAPOBJECT Yapısı
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: f41e02e7c528063f4b7ed485cbadbabb4d3e5ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801806"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="dc11d-103">COR_HEAPOBJECT Yapısı</span><span class="sxs-lookup"><span data-stu-id="dc11d-103">COR_HEAPOBJECT Structure</span></span>

<span data-ttu-id="dc11d-104">Yönetilen yığında bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc11d-104">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc11d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dc11d-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="dc11d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dc11d-106">Members</span></span>  
  
|<span data-ttu-id="dc11d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="dc11d-107">Member</span></span>|<span data-ttu-id="dc11d-108">Description</span><span class="sxs-lookup"><span data-stu-id="dc11d-108">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="dc11d-109">Bellekteki nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="dc11d-109">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="dc11d-110">Nesnenin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="dc11d-110">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="dc11d-111">Nesnenin türünü temsil eden bir [COR_TYPEID](cor-typeid-structure.md) belirteci.</span><span class="sxs-lookup"><span data-stu-id="dc11d-111">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc11d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc11d-112">Remarks</span></span>  

 <span data-ttu-id="dc11d-113">`COR_HEAPOBJECT`örnekler, [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi numaralandırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="dc11d-113">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="dc11d-114">`COR_HEAPOBJECT`Örnek, yönetilen yığında canlı bir nesne veya herhangi bir nesne tarafından kökü belirtilmemiş ancak çöp toplayıcı tarafından henüz toplanmayan bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc11d-114">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="dc11d-115">Daha iyi performans için, `COR_HEAPOBJECT.address` alan, `CORDB_ADDRESS` hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugValue arabirimi değeri yerine bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="dc11d-115">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="dc11d-116">Belirli bir nesne adresi için bir ICorDebugValue nesnesi almak üzere, `CORDB_ADDRESS` değeri [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc11d-116">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="dc11d-117">Daha iyi performans için, `COR_HEAPOBJECT.type` alan, `COR_TYPEID` hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugType arabirim değeri yerine bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="dc11d-117">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="dc11d-118">Verilen tür KIMLIĞI için bir ICorDebugType nesnesi elde etmek için, `COR_TYPEID` değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc11d-118">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="dc11d-119">`COR_HEAPOBJECT`Yapı, başvuru sayılı BIR com arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="dc11d-119">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="dc11d-120">`COR_HEAPOBJECT` [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) metodunu çağırarak numaralandırıcıdan bir örnek alırsanız, daha sonra başvuruyu serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc11d-120">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc11d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc11d-121">Requirements</span></span>  

 <span data-ttu-id="dc11d-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc11d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc11d-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc11d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc11d-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dc11d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc11d-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc11d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc11d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc11d-126">See also</span></span>

- [<span data-ttu-id="dc11d-127">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="dc11d-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="dc11d-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dc11d-128">Debugging</span></span>](index.md)
