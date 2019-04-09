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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103915"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="0fa44-102">ICorDebugProcess5::EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fa44-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="0fa44-103">Bir numaralandırıcı, yönetilen yığındaki nesneler için alır.</span><span class="sxs-lookup"><span data-stu-id="0fa44-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fa44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fa44-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fa44-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0fa44-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="0fa44-106">[out] Adresine bir işaretçi bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) bulunan yönetilen yığındaki nesneler için bir numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0fa44-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fa44-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0fa44-107">Remarks</span></span>  
 <span data-ttu-id="0fa44-108">Çağırmadan önce `ICorDebugProcess5::EnumerateHeap` yöntemini çağırmalıdır [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini incelemek `areGCStructuresValid` alan döndürülen [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnenin numaralandırılabilir çöp toplama yığınındaki geçerli durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0fa44-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="0fa44-109">Ayrıca, `ICorDebugProcess5::EnumerateHeap` döndürür `E_FAIL` için yönetilen yığında ayrılan bellek önce işlem ömrü içinde çok erken eklediğiniz durumunda.</span><span class="sxs-lookup"><span data-stu-id="0fa44-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="0fa44-110">[Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) arabirimi nesnedir listeleme olanak tanıyan Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0fa44-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="0fa44-111">Bu yöntem doldurur [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) koleksiyon nesnesi ile [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle tüm nesneler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fa44-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="0fa44-112">Koleksiyon de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) göre köklü olmayan olmayan nesneler hakkında bilgi sağlayan örnekleri nesnesi ancak henüz çöp toplayıcısı tarafından toplanmış değil.</span><span class="sxs-lookup"><span data-stu-id="0fa44-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fa44-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fa44-113">Requirements</span></span>  
 <span data-ttu-id="0fa44-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fa44-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fa44-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fa44-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fa44-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fa44-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0fa44-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0fa44-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0fa44-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fa44-118">See also</span></span>

- [<span data-ttu-id="0fa44-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0fa44-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="0fa44-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0fa44-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
