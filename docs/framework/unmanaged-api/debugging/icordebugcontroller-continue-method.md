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
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892859"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="2c24c-102">ICorDebugController::Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c24c-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="2c24c-103">[Durdurma yöntemine](icordebugcontroller-stop-method.md)yapılan çağrıdan sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="2c24c-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="2c24c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c24c-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="2c24c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c24c-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="2c24c-106">'ndaki Bant dışı `true` bir olaydan devam edildiğinde olarak ayarlayın; Aksi takdirde, olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2c24c-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c24c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c24c-107">Remarks</span></span>

<span data-ttu-id="2c24c-108">`Continue``ICorDebugController::Stop` yöntemine yapılan çağrıdan sonra işlemi devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="2c24c-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="2c24c-109">Karışık modda hata ayıklama yaparken, bir bant dışı olaydan `Continue` devam etmediğiniz takdirde Win32 olay iş parçacığı üzerinde çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="2c24c-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="2c24c-110">*Bant içi olay* , hata ayıklayıcının işlemin yönetilen durumuyla etkileşimi desteklediği yönetilen bir olaydır veya normal yönetilmeyen bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="2c24c-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="2c24c-111">Bu durumda, hata ayıklayıcı `fOutOfBand` `false` [ICorDebugUnmanagedCallback: parametresi olarak ayarlanmış:D ebugevent geri aramasını](icordebugunmanagedcallback-debugevent-method.md) alır.</span><span class="sxs-lookup"><span data-stu-id="2c24c-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="2c24c-112">*Bant dışı bir olay* , işlem olay nedeniyle durdurulduğunda işlemin yönetilen durumuyla etkileşimi mümkün olmadığı sürece yönetilmeyen bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="2c24c-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="2c24c-113">Bu durumda, hata ayıklayıcı `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` parametresi olarak ayarlanmış şekilde `true`geri çağırma işlemini alır.</span><span class="sxs-lookup"><span data-stu-id="2c24c-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c24c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c24c-114">Requirements</span></span>

<span data-ttu-id="2c24c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c24c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2c24c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c24c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2c24c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c24c-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2c24c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c24c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
