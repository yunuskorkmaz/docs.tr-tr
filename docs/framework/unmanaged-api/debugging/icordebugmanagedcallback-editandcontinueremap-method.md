---
description: ': ICorDebugManagedCallback:: EditAndContinueRemap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ad8932e41236cdb8ed213024efb4175292a5d5f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791016"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="122a2-103">ICorDebugManagedCallback::EditAndContinueRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="122a2-103">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="122a2-104">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="122a2-104">This method has been deprecated.</span></span> <span data-ttu-id="122a2-105">Hata ayıklayıcıya bir yeniden eşleme olayının tümleşik geliştirme ortamına (IDE) gönderildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="122a2-105">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122a2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="122a2-106">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="122a2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="122a2-107">Remarks</span></span>  

 <span data-ttu-id="122a2-108">`EditAndContinueRemap`Yöntemi, güncelleştirilmiş bir işlevin eski bir sürümündeki kodun yürütülmesi denendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="122a2-108">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="122a2-109">Ortak dil çalışma zamanı, `EditAndContinueRemap` IDE 'ye yeniden eşleme olayı göndermek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="122a2-109">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122a2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="122a2-110">Requirements</span></span>  

 <span data-ttu-id="122a2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122a2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122a2-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="122a2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="122a2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="122a2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="122a2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122a2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="122a2-115">See also</span></span>

- [<span data-ttu-id="122a2-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="122a2-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
