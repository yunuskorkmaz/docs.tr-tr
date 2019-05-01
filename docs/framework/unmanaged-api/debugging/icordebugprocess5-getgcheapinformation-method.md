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
ms.openlocfilehash: 50b682a7b3a4aadf7559120745265ef266cf2870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948752"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="eaa66-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="eaa66-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="eaa66-103">Şu anda numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaa66-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaa66-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eaa66-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="eaa66-106">[out] Bir işaretçi bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) çöp toplama yığınındaki hakkında genel bilgi sağlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="eaa66-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaa66-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eaa66-107">Remarks</span></span>  
 <span data-ttu-id="eaa66-108">`ICorDebugProcess5::GetGCHeapInformation` Çöp toplama işleminde yapıları emin olmak için tek tek yığın bölgeleri şu anda geçerli olan veya yığın numaralandırma önce metodu çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eaa66-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="eaa66-109">Bir toplama işlemi devam ederken, çöp toplama yığınındaki öğrendiniz olamaz.</span><span class="sxs-lookup"><span data-stu-id="eaa66-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="eaa66-110">Aksi takdirde, sabit listesi geçersiz çöp toplama yapıları yakalama.</span><span class="sxs-lookup"><span data-stu-id="eaa66-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa66-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaa66-111">Requirements</span></span>  
 <span data-ttu-id="eaa66-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaa66-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa66-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaa66-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaa66-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaa66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaa66-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa66-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaa66-116">See also</span></span>

- [<span data-ttu-id="eaa66-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaa66-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="eaa66-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eaa66-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
