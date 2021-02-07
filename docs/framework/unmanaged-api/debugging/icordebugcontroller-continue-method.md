---
description: ': ICorDebugController:: Continue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e5858a8c287e8dd5a493a85c9f427ad8acd9ecc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710809"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="eb0d8-103">ICorDebugController::Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb0d8-103">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="eb0d8-104">[Durdurma yöntemine](icordebugcontroller-stop-method.md)yapılan çağrıdan sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-104">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="eb0d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb0d8-105">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="eb0d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb0d8-106">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="eb0d8-107">'ndaki `true` Bant dışı bir olaydan devam edildiğinde olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="eb0d8-107">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb0d8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb0d8-108">Remarks</span></span>

<span data-ttu-id="eb0d8-109">`Continue` yöntemine yapılan çağrıdan sonra işlemi devam ettirir `ICorDebugController::Stop` .</span><span class="sxs-lookup"><span data-stu-id="eb0d8-109">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="eb0d8-110">Karışık modda hata ayıklama yaparken, `Continue` bir bant dışı olaydan devam etmediğiniz takdirde Win32 olay iş parçacığı üzerinde çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-110">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="eb0d8-111">*Bant içi olay* , hata ayıklayıcının işlemin yönetilen durumuyla etkileşimi desteklediği yönetilen bir olaydır veya normal yönetilmeyen bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-111">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="eb0d8-112">Bu durumda, hata ayıklayıcı [ICorDebugUnmanagedCallback: parametresi olarak ayarlanmış:D ebugEvent geri aramasını](icordebugunmanagedcallback-debugevent-method.md) alır `fOutOfBand` `false` .</span><span class="sxs-lookup"><span data-stu-id="eb0d8-112">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="eb0d8-113">*Bant dışı bir olay* , işlem olay nedeniyle durdurulduğunda işlemin yönetilen durumuyla etkileşimi mümkün olmadığı sürece yönetilmeyen bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-113">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="eb0d8-114">Bu durumda, hata ayıklayıcı `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` parametresi olarak ayarlanmış şekilde geri çağırma işlemini alır `true` .</span><span class="sxs-lookup"><span data-stu-id="eb0d8-114">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb0d8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb0d8-115">Requirements</span></span>

<span data-ttu-id="eb0d8-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb0d8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="eb0d8-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb0d8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="eb0d8-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb0d8-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="eb0d8-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0d8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
