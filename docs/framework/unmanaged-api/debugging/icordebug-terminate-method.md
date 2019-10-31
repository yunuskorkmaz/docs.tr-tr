---
title: ICorDebug::Terminate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 78838e9002cb3f5263395af9de255c54de47b6ae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134025"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="e2121-102">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2121-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="e2121-103">`ICorDebug` nesnesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e2121-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2121-104">hata ayıklamakta olan tüm işlemler için [ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) geri çağırması alınana kadar `Terminate` çağrılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2121-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2121-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2121-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e2121-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2121-106">Remarks</span></span>  
 <span data-ttu-id="e2121-107">`Terminate`, `ICorDebug` nesnesine artık gerek kalmadığında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2121-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2121-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2121-108">Requirements</span></span>  
 <span data-ttu-id="e2121-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2121-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2121-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2121-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2121-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2121-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2121-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2121-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2121-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2121-113">See also</span></span>

- [<span data-ttu-id="e2121-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2121-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
