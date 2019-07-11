---
title: ICorDebugProcess5::GetGCHeapInformation Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e94034fcdcd8d86f34c61af30a7729a80c913fac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767341"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="a0bc5-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="a0bc5-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="a0bc5-103">Şu anda numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0bc5-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0bc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0bc5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0bc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0bc5-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="a0bc5-106">[out] Bir işaretçi bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) çöp toplama yığınındaki hakkında genel bilgi sağlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="a0bc5-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0bc5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0bc5-107">Remarks</span></span>  
 <span data-ttu-id="a0bc5-108">`ICorDebugProcess5::GetGCHeapInformation` Çöp toplama işleminde yapıları emin olmak için tek tek yığın bölgeleri şu anda geçerli olan veya yığın numaralandırma önce metodu çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0bc5-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="a0bc5-109">Bir toplama işlemi devam ederken, çöp toplama yığınındaki öğrendiniz olamaz.</span><span class="sxs-lookup"><span data-stu-id="a0bc5-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="a0bc5-110">Aksi takdirde, sabit listesi geçersiz çöp toplama yapıları yakalama.</span><span class="sxs-lookup"><span data-stu-id="a0bc5-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0bc5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0bc5-111">Requirements</span></span>  
 <span data-ttu-id="a0bc5-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0bc5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0bc5-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0bc5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0bc5-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0bc5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0bc5-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0bc5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0bc5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0bc5-116">See also</span></span>

- [<span data-ttu-id="a0bc5-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0bc5-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="a0bc5-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a0bc5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
