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
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962696"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="7ae9f-102">ICorDebugStepper Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="7ae9f-103">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ae9f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ae9f-104">Methods</span></span>  
  
|<span data-ttu-id="7ae9f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ae9f-105">Method</span></span>|<span data-ttu-id="7ae9f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ae9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ae9f-107">Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="7ae9f-108">Bunun `ICorDebugStepper` , aldığı son adım komutunu iptal etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="7ae9f-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="7ae9f-110">Bu `ICorDebugStepper` , şu anda bir adım yürütüp yürütümeyeceğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="7ae9f-111">SetInterceptMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="7ae9f-112">İçine eklenen kod türlerini belirten bir Cordebugkesmenoktası değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="7ae9f-113">SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="7ae9f-114">[ICorDebugStepper:: StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göreli bağımsız değişken değerlerini veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) kodunu geçirip geçirmediğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="7ae9f-115">SetUnmappedStopMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="7ae9f-116">Yürütmenin durdurulacağı eşlenmemiş kodun türünü belirten bir CorDebugUnmappedStop değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="7ae9f-117">Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="7ae9f-118">Bunun `ICorDebugStepper` , kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="7ae9f-119">StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="7ae9f-120">Bunun `ICorDebugStepper` , kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="7ae9f-121">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ae9f-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="7ae9f-122">Bunun `ICorDebugStepper` , kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve belirtilen aralıkların en son ötesinde koda ulaştığında dönüşmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ae9f-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ae9f-123">Remarks</span></span>  
 <span data-ttu-id="7ae9f-124">`ICorDebugStepper` Arabirim aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="7ae9f-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="7ae9f-125">Verilen bir step komutu ve bu komutun tamamlanması arasında bir tanımlayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="7ae9f-126">Gerçekleştirilebilecek tüm adımlamayı kapsüllemek için merkezi bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="7ae9f-127">Bir atlama işlemini erken iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="7ae9f-128">İş parçacığı başına birden fazla Stepper olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="7ae9f-129">Örneğin, bir işlev üzerinde atlama sırasında bir kesme noktası isabet edebilir ve Kullanıcı bu işlevin içinde yeni bir Adımlama işlemi başlatmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="7ae9f-130">Bu durumun nasıl işleneceğini belirleme, hata ayıklayıcıya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="7ae9f-131">Hata ayıklayıcı orijinal atlama işlemini iptal etmek veya iki işlemi iç içe aktarmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="7ae9f-132">`ICorDebugStepper` Arabirim her iki seçeneği de destekler.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="7ae9f-133">Ortak dil çalışma zamanı (CLR), çapraz iş parçacıklı, sıralanmış bir çağrı yapıyorsa, iş parçacıkları arasında Stepper bir geçiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ae9f-134">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ae9f-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ae9f-135">Requirements</span></span>  
 <span data-ttu-id="7ae9f-136">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ae9f-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ae9f-137">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ae9f-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ae9f-138">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ae9f-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ae9f-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ae9f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae9f-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ae9f-140">See also</span></span>

- [<span data-ttu-id="7ae9f-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ae9f-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
