---
title: ICorDebugManagedCallback::Break Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83524b24fd05969fa4f45fd742d1df955c441d44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732394"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="e6097-102">ICorDebugManagedCallback::Break Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6097-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="e6097-103">Hata ayıklayıcı bildirir, bir <xref:System.Reflection.Emit.OpCodes.Break> yönerge kodu stream'de yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e6097-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6097-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6097-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6097-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6097-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="e6097-106">[in] Kesme yönergesine içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6097-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="e6097-107">[in] Bir işaretçi Icordebugthread nesneye kesme yönergesine içeren iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e6097-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6097-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6097-108">Requirements</span></span>  
 <span data-ttu-id="e6097-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6097-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6097-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6097-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6097-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6097-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6097-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6097-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6097-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6097-113">See also</span></span>
- [<span data-ttu-id="e6097-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6097-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
