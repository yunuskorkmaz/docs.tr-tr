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
ms.openlocfilehash: 321298ce942b35d11a861c87cdf6b8714179ea97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080845"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="5d531-102">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d531-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="5d531-103">Sonlandırır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="5d531-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d531-104">`Terminate` kadar çağrılmamalıdır bir [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) hata ayıklama gerçekleştirilen tüm işlemler için geri çağırma alınmış.</span><span class="sxs-lookup"><span data-stu-id="5d531-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d531-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d531-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5d531-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d531-106">Remarks</span></span>  
 <span data-ttu-id="5d531-107">`Terminate` ne zaman çağrılmalıdır `ICorDebug` nesne artık gerekli.</span><span class="sxs-lookup"><span data-stu-id="5d531-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d531-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d531-108">Requirements</span></span>  
 <span data-ttu-id="5d531-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d531-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d531-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d531-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d531-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d531-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d531-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d531-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d531-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d531-113">See also</span></span>

- [<span data-ttu-id="5d531-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d531-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
