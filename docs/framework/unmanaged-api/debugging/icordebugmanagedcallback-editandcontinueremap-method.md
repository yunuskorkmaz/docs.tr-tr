---
title: ICorDebugManagedCallback::EditAndContinueRemap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 100688ece4ebb984d3d03823ab01bbaae7d395db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760271"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="9055c-102">ICorDebugManagedCallback::EditAndContinueRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9055c-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="9055c-103">Bu yöntem kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9055c-103">This method has been deprecated.</span></span> <span data-ttu-id="9055c-104">Hata ayıklayıcı tümleşik geliştirme ortamı (IDE) için bir eşleme olay gönderildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="9055c-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9055c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9055c-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9055c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9055c-106">Remarks</span></span>  
 <span data-ttu-id="9055c-107">`EditAndContinueRemap` Yöntemi, güncelleştirilmiş bir işlevi daha eski bir sürümünde kod yürütmeyi denediğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9055c-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="9055c-108">Ortak dil çalışma zamanı çağrıları `EditAndContinueRemap` IDE'ye remap olay göndermek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9055c-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9055c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9055c-109">Requirements</span></span>  
 <span data-ttu-id="9055c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9055c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9055c-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9055c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9055c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9055c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9055c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9055c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9055c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9055c-114">See also</span></span>

- [<span data-ttu-id="9055c-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9055c-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
