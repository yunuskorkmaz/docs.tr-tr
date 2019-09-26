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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274030"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="c6deb-102">COR_HEAPOBJECT Yapısı</span><span class="sxs-lookup"><span data-stu-id="c6deb-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="c6deb-103">Yönetilen yığında bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6deb-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6deb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6deb-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="c6deb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c6deb-105">Members</span></span>  
  
|<span data-ttu-id="c6deb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c6deb-106">Member</span></span>|<span data-ttu-id="c6deb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6deb-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="c6deb-108">Bellekteki nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="c6deb-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="c6deb-109">Nesnenin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="c6deb-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="c6deb-110">Nesnenin türünü temsil eden bir [COR_TYPEID](cor-typeid-structure.md) belirteci.</span><span class="sxs-lookup"><span data-stu-id="c6deb-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6deb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6deb-111">Remarks</span></span>  
 <span data-ttu-id="c6deb-112">`COR_HEAPOBJECT`örnekler, [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi numaralandırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="c6deb-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="c6deb-113">`COR_HEAPOBJECT` Örnek, yönetilen yığında canlı bir nesne veya herhangi bir nesne tarafından kökü belirtilmemiş ancak çöp toplayıcı tarafından henüz toplanmayan bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6deb-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="c6deb-114">Daha iyi performans için, `COR_HEAPOBJECT.address` alan, hata `CORDB_ADDRESS` ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugValue arabirimi değeri yerine bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="c6deb-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="c6deb-115">Belirli bir nesne adresi için bir ICorDebugValue nesnesi almak üzere, `CORDB_ADDRESS` değeri [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6deb-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="c6deb-116">Daha iyi performans için, `COR_HEAPOBJECT.type` alan, hata `COR_TYPEID` ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugType arabirim değeri yerine bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="c6deb-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="c6deb-117">Verilen tür kimliği için bir ICorDebugType nesnesi elde etmek için, `COR_TYPEID` değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6deb-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="c6deb-118">Yapı `COR_HEAPOBJECT` , başvuru sayılı bir com arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="c6deb-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="c6deb-119">`COR_HEAPOBJECT` [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) metodunu çağırarak numaralandırıcıdan bir örnek alırsanız, daha sonra başvuruyu serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6deb-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6deb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6deb-120">Requirements</span></span>  
 <span data-ttu-id="c6deb-121">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6deb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6deb-122">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c6deb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6deb-123">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c6deb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6deb-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6deb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6deb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6deb-125">See also</span></span>

- [<span data-ttu-id="c6deb-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="c6deb-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c6deb-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c6deb-127">Debugging</span></span>](index.md)
