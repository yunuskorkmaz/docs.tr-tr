---
title: ICorDebugStepper::SetInterceptMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791764"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="9148b-102">ICorDebugStepper::SetInterceptMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9148b-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="9148b-103">İçine eklenen kod türlerini belirten bir değer belirler.</span><span class="sxs-lookup"><span data-stu-id="9148b-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9148b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9148b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9148b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9148b-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="9148b-106">'ndaki Kod türlerini belirten Cordebugkesmenoktası numaralandırması değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="9148b-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9148b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9148b-107">Remarks</span></span>  
 <span data-ttu-id="9148b-108">Bir yakalayıcıyı için bit ayarlandıysa, verilen bir işlem kodu türü ile karşılaşıldığında Stepper tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="9148b-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="9148b-109">Bit silinirse, kesintiye uğratan kod atlanır.</span><span class="sxs-lookup"><span data-stu-id="9148b-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="9148b-110">`SetInterceptMask` yöntemi, [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (kullanıcının Görünüm noktasından) ile öngörülemeyen etkileşimlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9148b-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="9148b-111">Örneğin, sınıf başlatma kodunun yalnızca görünür (diğer bir deyişle, iç olmayan) kısmı, bilgi ve STOP_NO_MAPPING_INFO ayarlanmamışsa (bkz. [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) yöntemi ve CorDebugUnmappedStop sabit listesi), Stepper sınıfı başlatma üzerinde adım adım olur.</span><span class="sxs-lookup"><span data-stu-id="9148b-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="9148b-112">Varsayılan olarak, `CorDebugIntercept` numaralandırmanın yalnızca INTERCEPT_NONE değeri kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="9148b-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9148b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9148b-113">Requirements</span></span>  
 <span data-ttu-id="9148b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9148b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9148b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9148b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9148b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9148b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9148b-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9148b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
