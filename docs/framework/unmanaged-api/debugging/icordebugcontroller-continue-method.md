---
title: ICorDebugController::Continue Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a4e98a7265bda288b20b1cee1a10ab11990e8e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748890"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="0339e-102">ICorDebugController::Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0339e-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="0339e-103">Yönetilen iş parçacıklarının yürütülmesini çağrısı yapıldıktan sonra sürdürür [Stop yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="0339e-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0339e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0339e-104">Syntax</span></span>  
  
```cpp  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0339e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0339e-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="0339e-106">[in] Kümesine `true` ; bir bant dışı olay devam etmesini, aksi takdirde, kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="0339e-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0339e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0339e-107">Remarks</span></span>  
 <span data-ttu-id="0339e-108">`Continue` işlem çağrısı yapıldıktan sonra devam eder `ICorDebugController::Stop` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0339e-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="0339e-109">Karışık mod hata ayıklaması yaparken çağırmayın `Continue` Win32'olay iş parçacığı sürece bir bant dışı olay devam ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="0339e-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="0339e-110">Bir *bant dışı olay* yönetilen bir olay ya da hata ayıklayıcı sırasında işlem yönetilen durumu ile etkileşimi destekleyen normal yönetilmeyen bir olay.</span><span class="sxs-lookup"><span data-stu-id="0339e-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="0339e-111">Bu durumda, hata ayıklayıcısı alıyor [Icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) geri çağırmayı kendi `fOutOfBand` parametresini `false`.</span><span class="sxs-lookup"><span data-stu-id="0339e-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="0339e-112">Bir *bant dışı olay* sırasında işlem yönetilen durumu ile etkileşimi olan imkansız olay nedeniyle işlem durdurulurken bir yönetilmeyen olaydır.</span><span class="sxs-lookup"><span data-stu-id="0339e-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="0339e-113">Bu durumda, hata ayıklayıcısı alıyor `ICorDebugUnmanagedCallback::DebugEvent` geri çağırmayı kendi `fOutOfBand` parametresini `true`.</span><span class="sxs-lookup"><span data-stu-id="0339e-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0339e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0339e-114">Requirements</span></span>  
 <span data-ttu-id="0339e-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0339e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0339e-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0339e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0339e-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0339e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0339e-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0339e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0339e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0339e-119">See also</span></span>
