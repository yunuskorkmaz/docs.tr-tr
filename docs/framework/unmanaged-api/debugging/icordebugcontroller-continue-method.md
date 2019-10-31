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
ms.openlocfilehash: 14356a12c944ef93dba5e7b818d3ee5cf5adc607
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125415"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="5bd37-102">ICorDebugController::Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bd37-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="5bd37-103">[Durdurma yöntemine](icordebugcontroller-stop-method.md)yapılan çağrıdan sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="5bd37-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="5bd37-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bd37-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="5bd37-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bd37-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="5bd37-106">'ndaki Bant dışı bir olaydan devam ederseniz `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5bd37-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bd37-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bd37-107">Remarks</span></span>

<span data-ttu-id="5bd37-108">`Continue` `ICorDebugController::Stop` yöntemine yapılan çağrıdan sonra işlem devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="5bd37-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="5bd37-109">Karışık modda hata ayıklama yaparken, bir bant dışı olaydan devam etmediğiniz takdirde Win32 olay iş parçacığında `Continue` ' ı çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="5bd37-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="5bd37-110">*Bant içi olay* , hata ayıklayıcının işlemin yönetilen durumuyla etkileşimi desteklediği yönetilen bir olaydır veya normal yönetilmeyen bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="5bd37-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="5bd37-111">Bu durumda, hata ayıklayıcı [ICorDebugUnmanagedCallback::D ebugEvent](icordebugunmanagedcallback-debugevent-method.md) geri aramasını alır `fOutOfBand` parametresi `false` olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5bd37-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="5bd37-112">*Bant dışı bir olay* , işlem olay nedeniyle durdurulduğunda işlemin yönetilen durumuyla etkileşimi mümkün olmadığı sürece yönetilmeyen bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="5bd37-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="5bd37-113">Bu durumda, hata ayıklayıcı `fOutOfBand` parametresiyle `true` olarak ayarlanan `ICorDebugUnmanagedCallback::DebugEvent` geri aramasını alır.</span><span class="sxs-lookup"><span data-stu-id="5bd37-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5bd37-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bd37-114">Requirements</span></span>

<span data-ttu-id="5bd37-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bd37-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5bd37-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5bd37-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5bd37-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5bd37-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5bd37-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd37-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
