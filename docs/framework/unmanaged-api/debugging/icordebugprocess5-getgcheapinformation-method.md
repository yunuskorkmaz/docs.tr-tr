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
ms.openlocfilehash: f8824ce004cac8bc2ad675c83dc6b5f167f183e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421053"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="9b408-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="9b408-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="9b408-103">Şu anda numaralandırılabilir olup olmadığını atık toplama yığın hakkında genel bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b408-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b408-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b408-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b408-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b408-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="9b408-106">[out] Bir işaretçi bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) değeri atık toplama yığın hakkında genel bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b408-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b408-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b408-107">Remarks</span></span>  
 <span data-ttu-id="9b408-108">`ICorDebugProcess5::GetGCHeapInformation` Öbek numaralandırma önce yöntemi çağrılmalıdır veya çöp toplama işleminde yapıları emin olmak için tek tek yığın bölgeler şu anda geçerli.</span><span class="sxs-lookup"><span data-stu-id="9b408-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="9b408-109">Bir koleksiyonu işlemi devam ederken atık toplama yığın gitti olamaz.</span><span class="sxs-lookup"><span data-stu-id="9b408-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="9b408-110">Aksi takdirde, numaralandırma geçersiz atık toplama yapıları yakalama.</span><span class="sxs-lookup"><span data-stu-id="9b408-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b408-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b408-111">Requirements</span></span>  
 <span data-ttu-id="9b408-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b408-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b408-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b408-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b408-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b408-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b408-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b408-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b408-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b408-116">See Also</span></span>  
 [<span data-ttu-id="9b408-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b408-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="9b408-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b408-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
