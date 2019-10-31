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
ms.openlocfilehash: 3fd1686eb268b9d4e347fe28e067a5321327dbd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137382"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="158be-102">ICorDebugManagedCallback::EditAndContinueRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="158be-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="158be-103">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="158be-103">This method has been deprecated.</span></span> <span data-ttu-id="158be-104">Hata ayıklayıcıya bir yeniden eşleme olayının tümleşik geliştirme ortamına (IDE) gönderildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="158be-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="158be-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="158be-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="158be-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="158be-106">Remarks</span></span>  
 <span data-ttu-id="158be-107">`EditAndContinueRemap` yöntemi, güncelleştirilmiş bir işlevin eski bir sürümündeki kodun yürütülmesi denendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="158be-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="158be-108">Ortak dil çalışma zamanı, IDE 'ye yeniden eşleme olayı göndermek için `EditAndContinueRemap` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="158be-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="158be-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="158be-109">Requirements</span></span>  
 <span data-ttu-id="158be-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="158be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="158be-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="158be-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="158be-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="158be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="158be-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="158be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158be-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="158be-114">See also</span></span>

- [<span data-ttu-id="158be-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="158be-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
