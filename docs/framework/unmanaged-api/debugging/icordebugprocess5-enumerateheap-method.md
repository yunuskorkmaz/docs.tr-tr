---
title: ICorDebugProcess5::EnumerateHeap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412ade32daaed4802215c628ab94b535fc542b93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423351"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="86f6e-102">ICorDebugProcess5::EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86f6e-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="86f6e-103">Bir numaralandırıcı nesneleri yönetilen yığında alır.</span><span class="sxs-lookup"><span data-stu-id="86f6e-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86f6e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86f6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86f6e-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="86f6e-106">[out] Adresine bir işaretçi bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) yönetilen öbek üzerinde bulunan nesneleri için bir numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="86f6e-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f6e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86f6e-107">Remarks</span></span>  
 <span data-ttu-id="86f6e-108">Çağırmadan önce `ICorDebugProcess5::EnumerateHeap` yöntemi çağırın [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini inceleyin `areGCStructuresValid` dönen alan [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Çöp toplama yığın mevcut durumunda numaralandırılabilir olduğundan emin olmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="86f6e-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="86f6e-109">Ayrıca, `ICorDebugProcess5::EnumerateHeap` döndürür `E_FAIL` yönetilen yığında ayrılan için bellek önce işlem ömrü içinde çok erken eklediğiniz durumunda.</span><span class="sxs-lookup"><span data-stu-id="86f6e-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="86f6e-110">[Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) arabiriminin nesnesidir Numaralandırılacak izin veren Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="86f6e-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="86f6e-111">Bu yöntem doldurur [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) koleksiyon nesnesi ile [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) tüm nesneler hakkında bilgi sağlayan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="86f6e-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="86f6e-112">Koleksiyon ayrıca içerebilir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) tarafından olsunlar olmayan nesneler hakkında bilgi sağlayan örnekleri nesne ancak henüz atık toplayıcısı tarafından toplanan değil.</span><span class="sxs-lookup"><span data-stu-id="86f6e-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f6e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86f6e-113">Requirements</span></span>  
 <span data-ttu-id="86f6e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f6e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f6e-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86f6e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86f6e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86f6e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f6e-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f6e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f6e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86f6e-118">See Also</span></span>  
 [<span data-ttu-id="86f6e-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86f6e-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="86f6e-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86f6e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
