---
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
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099072"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="70cde-102">COR_HEAPOBJECT Yapısı</span><span class="sxs-lookup"><span data-stu-id="70cde-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="70cde-103">Yönetilen yığında bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="70cde-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70cde-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="70cde-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="70cde-105">Members</span></span>  
  
|<span data-ttu-id="70cde-106">Üye</span><span class="sxs-lookup"><span data-stu-id="70cde-106">Member</span></span>|<span data-ttu-id="70cde-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70cde-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="70cde-108">Bellekteki nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="70cde-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="70cde-109">Nesnenin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="70cde-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="70cde-110">Nesnenin türünü temsil eden bir [COR_TYPEID](cor-typeid-structure.md) belirteci.</span><span class="sxs-lookup"><span data-stu-id="70cde-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70cde-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70cde-111">Remarks</span></span>  
 <span data-ttu-id="70cde-112">`COR_HEAPOBJECT` örnekleri, [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi numaralandırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="70cde-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="70cde-113">`COR_HEAPOBJECT` bir örnek, yönetilen yığında canlı bir nesne veya herhangi bir nesne tarafından kökü belirtilmemiş ancak atık toplayıcı tarafından henüz toplanmayan bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="70cde-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="70cde-114">Daha iyi performans için `COR_HEAPOBJECT.address` alanı, hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugValue arabirimi değeri yerine `CORDB_ADDRESS` bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="70cde-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="70cde-115">Belirli bir nesne adresi için bir ICorDebugValue nesnesi almak üzere `CORDB_ADDRESS` değerini [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70cde-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="70cde-116">Daha iyi performans için `COR_HEAPOBJECT.type` alanı, hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugType arabirim değeri yerine `COR_TYPEID` bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="70cde-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="70cde-117">Belirli bir tür KIMLIĞI için bir ICorDebugType nesnesi almak üzere `COR_TYPEID` değerini [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70cde-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="70cde-118">`COR_HEAPOBJECT` yapısı, başvuru sayılı bir COM arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="70cde-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="70cde-119">[ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) metodunu çağırarak numaralandırıcıda bir `COR_HEAPOBJECT` örneği alırsanız, daha sonra başvuruyu serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70cde-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70cde-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70cde-120">Requirements</span></span>  
 <span data-ttu-id="70cde-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cde-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cde-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70cde-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70cde-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="70cde-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70cde-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cde-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cde-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70cde-125">See also</span></span>

- [<span data-ttu-id="70cde-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="70cde-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="70cde-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="70cde-127">Debugging</span></span>](index.md)
