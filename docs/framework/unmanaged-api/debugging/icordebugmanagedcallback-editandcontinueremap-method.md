---
title: "ICorDebugManagedCallback::EditAndContinueRemap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EditAndContinueRemap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e45cf5376f0c8b4fbe76f56e3adcce22b1ef5c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="1e102-102">ICorDebugManagedCallback::EditAndContinueRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e102-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="1e102-103">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1e102-103">This method has been deprecated.</span></span> <span data-ttu-id="1e102-104">Hata ayıklayıcı eşleme olay tümleşik geliştirme ortamı (IDE) gönderilmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1e102-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e102-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e102-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1e102-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e102-106">Remarks</span></span>  
 <span data-ttu-id="1e102-107">`EditAndContinueRemap` Eski bir sürümüne güncelleştirilmiş bir işlevin içindeki kod yürütmeyi çalışırken yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1e102-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="1e102-108">Ortak dil çalışma zamanı çağrıları `EditAndContinueRemap` IDE eşleme olay göndermek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="1e102-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e102-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e102-109">Requirements</span></span>  
 <span data-ttu-id="1e102-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e102-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e102-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e102-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e102-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e102-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e102-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e102-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e102-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e102-114">See Also</span></span>  
 [<span data-ttu-id="1e102-115">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e102-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
