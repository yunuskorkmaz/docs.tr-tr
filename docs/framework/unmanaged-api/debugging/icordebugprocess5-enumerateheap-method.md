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
ms.openlocfilehash: 1b404b7762e085eb44f0bd3b448fcee9eab9a3c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948791"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="67ada-102">ICorDebugProcess5::EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67ada-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="67ada-103">Bir numaralandırıcı, yönetilen yığındaki nesneler için alır.</span><span class="sxs-lookup"><span data-stu-id="67ada-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ada-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67ada-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67ada-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67ada-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="67ada-106">[out] Adresine bir işaretçi bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) bulunan yönetilen yığındaki nesneler için bir numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="67ada-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67ada-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67ada-107">Remarks</span></span>  
 <span data-ttu-id="67ada-108">Çağırmadan önce `ICorDebugProcess5::EnumerateHeap` yöntemini çağırmalıdır [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini incelemek `areGCStructuresValid` alan döndürülen [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnenin numaralandırılabilir çöp toplama yığınındaki geçerli durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="67ada-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="67ada-109">Ayrıca, `ICorDebugProcess5::EnumerateHeap` döndürür `E_FAIL` için yönetilen yığında ayrılan bellek önce işlem ömrü içinde çok erken eklediğiniz durumunda.</span><span class="sxs-lookup"><span data-stu-id="67ada-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="67ada-110">[Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) arabirimi nesnedir listeleme olanak tanıyan Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="67ada-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="67ada-111">Bu yöntem doldurur [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) koleksiyon nesnesi ile [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle tüm nesneler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67ada-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="67ada-112">Koleksiyon de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) göre köklü olmayan olmayan nesneler hakkında bilgi sağlayan örnekleri nesnesi ancak henüz çöp toplayıcısı tarafından toplanmış değil.</span><span class="sxs-lookup"><span data-stu-id="67ada-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ada-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67ada-113">Requirements</span></span>  
 <span data-ttu-id="67ada-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ada-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ada-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67ada-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67ada-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67ada-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67ada-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ada-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ada-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67ada-118">See also</span></span>

- [<span data-ttu-id="67ada-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67ada-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="67ada-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67ada-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
