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
ms.openlocfilehash: a236103b8ca1501ae4c9109c1fd9e78865ab9c9c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740593"
---
# <a name="corheapobject-structure"></a><span data-ttu-id="02bce-102">COR_HEAPOBJECT Yapısı</span><span class="sxs-lookup"><span data-stu-id="02bce-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="02bce-103">Yönetilen yığındaki bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="02bce-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02bce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02bce-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="02bce-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="02bce-105">Members</span></span>  
  
|<span data-ttu-id="02bce-106">Üye</span><span class="sxs-lookup"><span data-stu-id="02bce-106">Member</span></span>|<span data-ttu-id="02bce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02bce-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="02bce-108">Bellekteki nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="02bce-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="02bce-109">Nesnesinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="02bce-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="02bce-110">A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) nesnenin türünü temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="02bce-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02bce-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02bce-111">Remarks</span></span>  
 <span data-ttu-id="02bce-112">`COR_HEAPOBJECT` örnekleri numaralandırarak alınabilir bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) çağırarak doldurulur arabirimi nesnesi [Icordebugprocess5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02bce-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="02bce-113">A `COR_HEAPOBJECT` örneği, yönetilen yığındaki bir canlı nesne hakkında ya da herhangi bir nesne tarafından kökü belirtilmemiş ancak henüz çöp toplayıcısı tarafından toplanmış değil bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="02bce-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="02bce-114">Daha iyi performans için `COR_HEAPOBJECT.address` alan bir `CORDB_ADDRESS` değeri yerine Icordebugvalue arabirimi hata ayıklama API çoğunu kullanılan değer.</span><span class="sxs-lookup"><span data-stu-id="02bce-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="02bce-115">Icordebugvalue nesnenin verilen nesnenin adresini almak için geçirebilirsiniz `CORDB_ADDRESS` değerini [Icordebugprocess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02bce-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="02bce-116">Daha iyi performans için `COR_HEAPOBJECT.type` alan bir `COR_TYPEID` değeri yerine Icordebugtype arabirimi hata ayıklama API çoğunu kullanılan değer.</span><span class="sxs-lookup"><span data-stu-id="02bce-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="02bce-117">Icordebugtype nesneyi bir verilen tür Kimliğini almak için geçirebilirsiniz `COR_TYPEID` değerini [Icordebugprocess5::gettypefortypeıd](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02bce-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="02bce-118">`COR_HEAPOBJECT` Yapısı başvuru sayılan bir COM arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="02bce-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="02bce-119">Aldığınız varsa bir `COR_HEAPOBJECT` çağırarak numaralandırıcı örneğinden [Icordebugheapenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) yöntemi, başvuru daha sonra serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="02bce-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02bce-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02bce-120">Requirements</span></span>  
 <span data-ttu-id="02bce-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02bce-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02bce-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02bce-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02bce-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02bce-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02bce-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02bce-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bce-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02bce-125">See also</span></span>

- [<span data-ttu-id="02bce-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="02bce-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="02bce-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="02bce-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
