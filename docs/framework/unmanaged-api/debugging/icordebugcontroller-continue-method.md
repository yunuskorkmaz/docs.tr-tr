---
title: "ICorDebugController::Continue Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="d3189-102">ICorDebugController::Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3189-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="d3189-103">Yönetilen iş parçacığı yürütülmesi için bir çağrı sonra sürdürür [Stop yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="d3189-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3189-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3189-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3189-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3189-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="d3189-106">[in] Kümesine `true` bir bant dışı olayından; etmeden, aksi takdirde kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="d3189-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3189-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3189-107">Remarks</span></span>  
 <span data-ttu-id="d3189-108">`Continue`Çağrı sonra işlemine devam `ICorDebugController::Stop` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3189-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="d3189-109">Karışık mod hata ayıklaması yaparken çağırmayın `Continue` Win32'olay iş parçacığı sürece bir bant dışı olayından devam ediliyor.</span><span class="sxs-lookup"><span data-stu-id="d3189-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="d3189-110">Bir *bant dışı olay* yönetilen bir olay ya da normal bir yönetilmeyen olay hata ayıklayıcı sırasında işlem yönetilen durumu ile etkileşimi destekler.</span><span class="sxs-lookup"><span data-stu-id="d3189-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="d3189-111">Bu durumda, hata ayıklayıcısı alıyor [Icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) geri çağırmayı kendi `fOutOfBand` parametre kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="d3189-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="d3189-112">Bir *bant dışı olay* sırasında işleminin yönetilen durumunu etkileşim olduğu imkansız işlem olayı nedeniyle durdurulurken bir yönetilmeyen olaydır.</span><span class="sxs-lookup"><span data-stu-id="d3189-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="d3189-113">Bu durumda, hata ayıklayıcısı alıyor `ICorDebugUnmanagedCallback::DebugEvent` geri çağırmayı kendi `fOutOfBand` parametre kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="d3189-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3189-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3189-114">Requirements</span></span>  
 <span data-ttu-id="d3189-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3189-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3189-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3189-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3189-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3189-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3189-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3189-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3189-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3189-119">See Also</span></span>  
 
