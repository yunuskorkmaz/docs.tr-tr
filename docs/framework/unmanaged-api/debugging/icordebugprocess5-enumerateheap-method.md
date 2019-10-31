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
ms.openlocfilehash: c8cfc9cdf6580a002f6ac15080012a9e8c63be20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129656"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="cc567-102">ICorDebugProcess5::EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc567-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="cc567-103">Yönetilen yığındaki nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="cc567-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc567-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc567-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc567-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc567-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="cc567-106">dışı Yönetilen yığında bulunan nesneler için bir Numaralandırıcı olan [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc567-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc567-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc567-107">Remarks</span></span>  
 <span data-ttu-id="cc567-108">`ICorDebugProcess5::EnumerateHeap` yöntemi çağrılmadan önce, [ICorDebugProcess5:: GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve döndürülen [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnesinin `areGCStructuresValid` alanının değerini inceleyerek, çöp toplama işleminin geçerli durum Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc567-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="cc567-109">Ayrıca, `ICorDebugProcess5::EnumerateHeap`, yönetilen yığın için bellekten önce, işlemin kullanım ömrü içinde çok erken bir şekilde iliştiriyorsa `E_FAIL` döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc567-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="cc567-110">[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) arabirimi nesnesi, [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesnelerini Listeletmanızı sağlayan ıcordebugger genum arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="cc567-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="cc567-111">Bu yöntem, [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) toplama nesnesini tüm nesneler hakkında bilgi sağlayan [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="cc567-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="cc567-112">Koleksiyon, herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmamış nesneler hakkında bilgi sağlayan [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cc567-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc567-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc567-113">Requirements</span></span>  
 <span data-ttu-id="cc567-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc567-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc567-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc567-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc567-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc567-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc567-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc567-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc567-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc567-118">See also</span></span>

- [<span data-ttu-id="cc567-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc567-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="cc567-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc567-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
