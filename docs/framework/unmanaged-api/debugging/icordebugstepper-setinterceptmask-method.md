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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a9d287e6520f1fc7826d85dfbcd8e9a6da22f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481081"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="6a9f8-102">ICorDebugStepper::SetInterceptMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a9f8-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="6a9f8-103">İçine girdiğiniz kod türlerini belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6a9f8-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a9f8-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a9f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a9f8-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="6a9f8-106">[in] Kod türlerini belirtir Cordebugıntercept sabit listesi değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6a9f8-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9f8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a9f8-107">Remarks</span></span>  
 <span data-ttu-id="6a9f8-108">Bir dinleyiciyi bitini ayarlarsanız, verilen kod kesintiye türünü karşılaşıldığında Adımlayıcı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="6a9f8-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="6a9f8-109">Araya giren kodu bit işaretli değilse, atlanacak.</span><span class="sxs-lookup"><span data-stu-id="6a9f8-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="6a9f8-110">`SetInterceptMask` Yöntemi olabilir öngörülemeyen etkileşim [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (açısından kullanıcının).</span><span class="sxs-lookup"><span data-stu-id="6a9f8-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="6a9f8-111">Örneğin, yalnızca görünür (diğer bir deyişle, iç olmayan) sınıf başlatma kodu kısmı eksik eşleme bilgilerini ve STOP_NO_MAPPING_INFO ayarlanmamış (bkz [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) yöntemi ve CorDebugUnmappedStop numaralandırması için) sınıf başlatma Adımlayıcı adım adım anlatır.</span><span class="sxs-lookup"><span data-stu-id="6a9f8-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="6a9f8-112">Varsayılan olarak, yalnızca INTERCEPT_NONE değerini `CorDebugIntercept` sabit listesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a9f8-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9f8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a9f8-113">Requirements</span></span>  
 <span data-ttu-id="6a9f8-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a9f8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9f8-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a9f8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a9f8-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9f8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9f8-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9f8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
