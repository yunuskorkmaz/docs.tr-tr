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
ms.openlocfilehash: 057ee7a323a8a725ebf82ee9dbaea61a43c061ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674615"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="070ba-102">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="070ba-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="070ba-103">Sonlandırır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="070ba-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="070ba-104">`Terminate` kadar çağrılmamalıdır bir [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) hata ayıklama gerçekleştirilen tüm işlemler için geri çağırma alınmış.</span><span class="sxs-lookup"><span data-stu-id="070ba-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070ba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="070ba-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="070ba-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="070ba-106">Remarks</span></span>  
 <span data-ttu-id="070ba-107">`Terminate` ne zaman çağrılmalıdır `ICorDebug` nesne artık gerekli.</span><span class="sxs-lookup"><span data-stu-id="070ba-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="070ba-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="070ba-108">Requirements</span></span>  
 <span data-ttu-id="070ba-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="070ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="070ba-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="070ba-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="070ba-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="070ba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="070ba-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="070ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070ba-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="070ba-113">See also</span></span>
- [<span data-ttu-id="070ba-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="070ba-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
