---
title: "ICorDebugController::SetAllThreadsDebugState Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.SetAllThreadsDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5a033ef2efd8fa5e3b519e19b62ce2dfb84a5e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="61171-102">ICorDebugController::SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61171-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="61171-103">Tüm yönetilen iş parçacığı hata ayıklama durumunu işleminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61171-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61171-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61171-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61171-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61171-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="61171-106">[in] Hata ayıklama için iş parçacığı durumunu belirtir "CorDebugThreadState" numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="61171-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="61171-107">[in] Hata ayıklama durumu ayarından muaf için bir iş parçacığı temsil eden bir "ICorDebugThread" nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61171-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="61171-108">Bu değer null ise, hiçbir iş parçacığı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="61171-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61171-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61171-109">Remarks</span></span>  
 <span data-ttu-id="61171-110">`SetAllThreadsDebugState` Yöntemi aracılığıyla görünür olmayan iş parçacıklarının etkileyebilir [EnumerateThreads yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), ile askıya alınan bunu iş parçacığı `SetAllThreadsDebugState` yöntemi ile devam ettirilebilir gerekecektir `SetAllThreadsDebugState` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61171-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61171-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61171-111">Requirements</span></span>  
 <span data-ttu-id="61171-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61171-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61171-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61171-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61171-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61171-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61171-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61171-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61171-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61171-116">See Also</span></span>  
 
