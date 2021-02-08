---
description: 'Daha fazla bilgi edinin: ICorDebugStepper Interface'
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
ms.openlocfilehash: a16df9d25b4d87b0638448c1fdf8fec4759261d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803600"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="a1d8d-103">ICorDebugStepper Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-103">ICorDebugStepper Interface</span></span>

<span data-ttu-id="a1d8d-104">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-104">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1d8d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a1d8d-105">Methods</span></span>  
  
|<span data-ttu-id="a1d8d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a1d8d-106">Method</span></span>|<span data-ttu-id="a1d8d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d8d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1d8d-108">Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-108">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="a1d8d-109">Bunun `ICorDebugStepper` , aldığı son adım komutunu iptal etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-109">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="a1d8d-110">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-110">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="a1d8d-111">Bu `ICorDebugStepper` , şu anda bir adım yürütüp yürütümeyeceğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-111">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="a1d8d-112">SetInterceptMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-112">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="a1d8d-113">İçine eklenen kod türlerini belirten bir Cordebugkesmenoktası değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-113">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="a1d8d-114">SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-114">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="a1d8d-115">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göreli bağımsız değişken değerlerini veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) kodunu geçirip geçirmediğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-115">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="a1d8d-116">SetUnmappedStopMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-116">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="a1d8d-117">Yürütmenin durdurulacağı eşlenmemiş kodun türünü belirten bir CorDebugUnmappedStop değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-117">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="a1d8d-118">Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-118">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="a1d8d-119">Bunun, `ICorDebugStepper` kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-119">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="a1d8d-120">StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-120">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="a1d8d-121">Bunun `ICorDebugStepper` , kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-121">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="a1d8d-122">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8d-122">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="a1d8d-123">Bunun `ICorDebugStepper` , kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve belirtilen aralıkların en son ötesinde koda ulaştığında dönüşmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-123">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1d8d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1d8d-124">Remarks</span></span>  

 <span data-ttu-id="a1d8d-125">`ICorDebugStepper`Arabirim aşağıdaki amaçlara hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="a1d8d-125">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="a1d8d-126">Verilen bir step komutu ve bu komutun tamamlanması arasında bir tanımlayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-126">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="a1d8d-127">Gerçekleştirilebilecek tüm adımlamayı kapsüllemek için merkezi bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-127">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="a1d8d-128">Bir atlama işlemini erken iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-128">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="a1d8d-129">İş parçacığı başına birden fazla Stepper olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-129">There can be more than one stepper per thread.</span></span> <span data-ttu-id="a1d8d-130">Örneğin, bir işlev üzerinde atlama sırasında bir kesme noktası isabet edebilir ve Kullanıcı bu işlevin içinde yeni bir Adımlama işlemi başlatmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-130">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="a1d8d-131">Bu durumun nasıl işleneceğini belirleme, hata ayıklayıcıya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-131">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="a1d8d-132">Hata ayıklayıcı orijinal atlama işlemini iptal etmek veya iki işlemi iç içe aktarmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-132">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="a1d8d-133">`ICorDebugStepper`Arabirim her iki seçeneği de destekler.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-133">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="a1d8d-134">Ortak dil çalışma zamanı (CLR), çapraz iş parçacıklı, sıralanmış bir çağrı yapıyorsa, iş parçacıkları arasında Stepper bir geçiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-134">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1d8d-135">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d8d-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1d8d-136">Requirements</span></span>  

 <span data-ttu-id="a1d8d-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1d8d-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1d8d-138">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1d8d-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1d8d-139">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a1d8d-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1d8d-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1d8d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d8d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d8d-141">See also</span></span>

- [<span data-ttu-id="a1d8d-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a1d8d-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
