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
ms.openlocfilehash: bf3d362902eb338e5d797b66c5fe2af4f3e1ae9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508333"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="e60b0-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="e60b0-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="e60b0-103">Şu anda numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e60b0-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e60b0-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e60b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e60b0-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="e60b0-106">[out] Bir işaretçi bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) çöp toplama yığınındaki hakkında genel bilgi sağlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="e60b0-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e60b0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e60b0-107">Remarks</span></span>  
 <span data-ttu-id="e60b0-108">`ICorDebugProcess5::GetGCHeapInformation` Çöp toplama işleminde yapıları emin olmak için tek tek yığın bölgeleri şu anda geçerli olan veya yığın numaralandırma önce metodu çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e60b0-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="e60b0-109">Bir toplama işlemi devam ederken, çöp toplama yığınındaki öğrendiniz olamaz.</span><span class="sxs-lookup"><span data-stu-id="e60b0-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="e60b0-110">Aksi takdirde, sabit listesi geçersiz çöp toplama yapıları yakalama.</span><span class="sxs-lookup"><span data-stu-id="e60b0-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e60b0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e60b0-111">Requirements</span></span>  
 <span data-ttu-id="e60b0-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e60b0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e60b0-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e60b0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e60b0-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e60b0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e60b0-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e60b0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60b0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e60b0-116">See also</span></span>
- [<span data-ttu-id="e60b0-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e60b0-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e60b0-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e60b0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
