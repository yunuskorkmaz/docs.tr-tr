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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3037fc704ffc3aac4d050cef7857261f138f7d35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738063"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="476a5-102">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="476a5-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="476a5-103">Sonlandırır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="476a5-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="476a5-104">`Terminate` kadar çağrılmamalıdır bir [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) hata ayıklama gerçekleştirilen tüm işlemler için geri çağırma alınmış.</span><span class="sxs-lookup"><span data-stu-id="476a5-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476a5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="476a5-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="476a5-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="476a5-106">Remarks</span></span>  
 <span data-ttu-id="476a5-107">`Terminate` ne zaman çağrılmalıdır `ICorDebug` nesne artık gerekli.</span><span class="sxs-lookup"><span data-stu-id="476a5-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="476a5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="476a5-108">Requirements</span></span>  
 <span data-ttu-id="476a5-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="476a5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="476a5-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="476a5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="476a5-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="476a5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="476a5-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="476a5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476a5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="476a5-113">See also</span></span>

- [<span data-ttu-id="476a5-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="476a5-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
