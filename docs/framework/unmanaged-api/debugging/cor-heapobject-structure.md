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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179331"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="cbc07-102">COR_HEAPOBJECT Yapısı</span><span class="sxs-lookup"><span data-stu-id="cbc07-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="cbc07-103">Yönetilen yığındaki bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbc07-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbc07-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="cbc07-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cbc07-105">Members</span></span>  
  
|<span data-ttu-id="cbc07-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cbc07-106">Member</span></span>|<span data-ttu-id="cbc07-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbc07-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="cbc07-108">Bellekteki nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="cbc07-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="cbc07-109">Nesnenin toplam boyutu, baytlar içinde.</span><span class="sxs-lookup"><span data-stu-id="cbc07-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="cbc07-110">Nesnenin türünü temsil eden [COR_TYPEID](cor-typeid-structure.md) belirteci.</span><span class="sxs-lookup"><span data-stu-id="cbc07-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc07-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbc07-111">Remarks</span></span>  
 <span data-ttu-id="cbc07-112">`COR_HEAPOBJECT`örnekler [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi ni arayarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirim nesnesini sayısallandırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="cbc07-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="cbc07-113">Örnek, `COR_HEAPOBJECT` yönetilen yığındaki canlı bir nesne veya herhangi bir nesne tarafından köklü olmayan ancak çöp toplayıcı tarafından henüz toplanmamış bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbc07-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="cbc07-114">Daha iyi performans `COR_HEAPOBJECT.address` için `CORDB_ADDRESS` alan, hata ayıklama API'sinin çoğunda kullanılan ICorDebugValue arabirim değeri yerine bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="cbc07-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="cbc07-115">Belirli bir nesne adresi için bir ICorDebugValue nesnesi elde etmek `CORDB_ADDRESS` için, değeri [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc07-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="cbc07-116">Daha iyi performans `COR_HEAPOBJECT.type` için `COR_TYPEID` alan, hata ayıklama API'sinin çoğunda kullanılan ICorDebugType arabirim değeri yerine bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="cbc07-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="cbc07-117">Belirli bir tür kimliği için bir ICorDebugType nesnesi elde etmek `COR_TYPEID` için, değeri [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc07-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="cbc07-118">Yapı, `COR_HEAPOBJECT` referans sayılan com arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="cbc07-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="cbc07-119">`COR_HEAPOBJECT` [ICorDebugHeapEnum::Sonraki](icordebugheapenum-next-method.md) yöntem çağırarak enumerator bir örnek alırsanız, daha sonra başvuru serbest gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbc07-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbc07-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbc07-120">Requirements</span></span>  
 <span data-ttu-id="cbc07-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbc07-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbc07-122">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbc07-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbc07-123">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbc07-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbc07-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbc07-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc07-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbc07-125">See also</span></span>

- [<span data-ttu-id="cbc07-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="cbc07-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="cbc07-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="cbc07-127">Debugging</span></span>](index.md)
