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
ms.openlocfilehash: 2c2b590e7402bf29ffeb5bd14fc383edae41a04e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404007"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="bdd81-102">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdd81-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="bdd81-103">Sonlandırır `ICorDebug` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bdd81-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd81-104">`Terminate` kadar çağrılmamalıdır bir [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) ayıklanacak tüm işlemler için geri çağırma alınmış.</span><span class="sxs-lookup"><span data-stu-id="bdd81-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd81-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdd81-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bdd81-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdd81-106">Remarks</span></span>  
 <span data-ttu-id="bdd81-107">`Terminate` ne zaman çağrılmalıdır `ICorDebug` nesne artık gerekli.</span><span class="sxs-lookup"><span data-stu-id="bdd81-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd81-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdd81-108">Requirements</span></span>  
 <span data-ttu-id="bdd81-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdd81-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd81-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdd81-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdd81-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdd81-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdd81-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd81-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bdd81-113">See Also</span></span>  
 [<span data-ttu-id="bdd81-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bdd81-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
