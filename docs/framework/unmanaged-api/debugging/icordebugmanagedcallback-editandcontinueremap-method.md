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
ms.openlocfilehash: 1d8aa2cca9dbbeaa9e03813b177ca59125770803
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721289"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="0b53e-102">ICorDebugManagedCallback::EditAndContinueRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b53e-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="0b53e-103">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0b53e-103">This method has been deprecated.</span></span> <span data-ttu-id="0b53e-104">Hata ayıklayıcıya bir yeniden eşleme olayının tümleşik geliştirme ortamına (IDE) gönderildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b53e-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b53e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b53e-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b53e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b53e-106">Remarks</span></span>  

 <span data-ttu-id="0b53e-107">`EditAndContinueRemap`Yöntemi, güncelleştirilmiş bir işlevin eski bir sürümündeki kodun yürütülmesi denendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0b53e-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="0b53e-108">Ortak dil çalışma zamanı, `EditAndContinueRemap` IDE 'ye yeniden eşleme olayı göndermek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0b53e-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b53e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b53e-109">Requirements</span></span>  

 <span data-ttu-id="0b53e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b53e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b53e-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b53e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b53e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b53e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b53e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b53e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b53e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b53e-114">See also</span></span>

- [<span data-ttu-id="0b53e-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b53e-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
