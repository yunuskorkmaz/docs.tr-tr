---
title: ICorDebugStepper Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bd650178c787440941b9fd9a84b1e85c55aac61
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973723"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="d727e-102">ICorDebugStepper Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d727e-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="d727e-103">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d727e-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d727e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d727e-104">Methods</span></span>  
  
|<span data-ttu-id="d727e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d727e-105">Method</span></span>|<span data-ttu-id="d727e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d727e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d727e-107">Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="d727e-108">Bu neden `ICorDebugStepper` aldığı son adım komutunu iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="d727e-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="d727e-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="d727e-110">Belirten bir değer alır olup bu `ICorDebugStepper` bir adımı yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="d727e-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="d727e-111">SetInterceptMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="d727e-112">İçine girdiğiniz kod türlerini belirten bir Cordebugıntercept değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d727e-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="d727e-113">SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="d727e-114">Belirten bir değeri ayarlar olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) aracılığıyla basamaklı yöntemin Microsoft Ara dili (MSIL) kodu veya yerel koda göre bağımsız değişken değerlerini geçirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d727e-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="d727e-115">SetUnmappedStopMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="d727e-116">Yürütmeyi durdur eşlenmemiş kodun türünü belirten bir CorDebugUnmappedStop değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d727e-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="d727e-117">Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="d727e-118">Bu neden olur `ICorDebugStepper` tek adımlı içeren kendi iş parçacığı aracılığıyla ve isteğe bağlı olarak için için iş parçacığının içinden çağıran işlevler aracılığıyla tek Adımlama devam edin.</span><span class="sxs-lookup"><span data-stu-id="d727e-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="d727e-119">StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="d727e-120">Bu neden `ICorDebugStepper` içeren kendi iş parçacığı aracılığıyla tek adımlı ve tam olduğunda geçerli çerçeve arama çerçeveye denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d727e-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="d727e-121">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d727e-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="d727e-122">Bu neden `ICorDebugStepper` isteğe bağlı olarak tek-adım içeren kendi iş parçacığı ve ne zaman döndürmek için son belirtilen aralıkların dışında kod ulaşır.</span><span class="sxs-lookup"><span data-stu-id="d727e-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d727e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d727e-123">Remarks</span></span>  
 <span data-ttu-id="d727e-124">`ICorDebugStepper` Arabirimi aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="d727e-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="d727e-125">Verilen bir adım komut ve bu komutun tamamlanması arasında bir tanımlayıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="d727e-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="d727e-126">Bunu gerçekleştirilebilecek tüm Adımlama kapsüllemek için merkezi bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d727e-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="d727e-127">Erken bir atlama işlemi iptal etmek için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="d727e-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="d727e-128">İş parçacığı başına birden fazla adımlayıcıdaki olabilir.</span><span class="sxs-lookup"><span data-stu-id="d727e-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="d727e-129">Örneğin, bir işlevin üzerine erişilince bir kesme noktası isabet ve bu işlevin içindeki yeni bir atlama işlemi başlatmak kullanıcı isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="d727e-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="d727e-130">Bu durumu yönetmek nasıl belirlemek için hata ayıklayıcı kadar var.</span><span class="sxs-lookup"><span data-stu-id="d727e-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="d727e-131">Hata ayıklayıcı özgün atlama işlemi iptal etmek veya iki işlem iç içe isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d727e-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="d727e-132">`ICorDebugStepper` Arabirimi iki seçeneği destekler.</span><span class="sxs-lookup"><span data-stu-id="d727e-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="d727e-133">Ortak dil çalışma zamanı (CLR) arası iş parçacıklı, sıralanmış bir çağrı yaparsa Adımlayıcı iş parçacıkları arasında taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d727e-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d727e-134">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d727e-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d727e-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d727e-135">Requirements</span></span>  
 <span data-ttu-id="d727e-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d727e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d727e-137">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d727e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d727e-138">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d727e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d727e-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d727e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d727e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d727e-140">See also</span></span>
- [<span data-ttu-id="d727e-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d727e-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
