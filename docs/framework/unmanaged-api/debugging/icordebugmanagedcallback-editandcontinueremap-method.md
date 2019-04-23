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
ms.openlocfilehash: d1bdb14e8c3a61a2b94cef778660eeb5c85c34df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149779"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="cd9b3-102">ICorDebugManagedCallback::EditAndContinueRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd9b3-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="cd9b3-103">Bu yöntem kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-103">This method has been deprecated.</span></span> <span data-ttu-id="cd9b3-104">Hata ayıklayıcı tümleşik geliştirme ortamı (IDE) için bir eşleme olay gönderildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9b3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd9b3-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd9b3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd9b3-106">Remarks</span></span>  
 <span data-ttu-id="cd9b3-107">`EditAndContinueRemap` Yöntemi, güncelleştirilmiş bir işlevi daha eski bir sürümünde kod yürütmeyi denediğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="cd9b3-108">Ortak dil çalışma zamanı çağrıları `EditAndContinueRemap` IDE'ye remap olay göndermek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9b3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd9b3-109">Requirements</span></span>  
 <span data-ttu-id="cd9b3-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9b3-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd9b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd9b3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd9b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd9b3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9b3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-114">See also</span></span>

- [<span data-ttu-id="cd9b3-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd9b3-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
