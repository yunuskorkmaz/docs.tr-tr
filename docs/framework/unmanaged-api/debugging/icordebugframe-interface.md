---
title: Icordebugframe Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame
helpviewer_keywords: ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2acc825f6592eae80f67e7614ca45f175b6756d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="e94fe-102">Icordebugframe Interface1</span><span class="sxs-lookup"><span data-stu-id="e94fe-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="e94fe-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e94fe-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e94fe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e94fe-104">Methods</span></span>  
  
|<span data-ttu-id="e94fe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e94fe-105">Method</span></span>|<span data-ttu-id="e94fe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e94fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e94fe-107">CreateStepper yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="e94fe-108">Bu göreli sürüm işlemlerini gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="e94fe-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="e94fe-109">GetCallee yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="e94fe-110">Bir işaretçi alır `ICorDebugFrame` bu çerçeve olarak adlandırılan veya bu döndürür null ise zincirde en içteki çerçeve geçerli zincirindeki.</span><span class="sxs-lookup"><span data-stu-id="e94fe-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="e94fe-111">GetCaller yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="e94fe-112">Bir işaretçi alır `ICorDebugFrame` geçerli zincirde bu çerçeve denilen ya da bu döndürür null ise zincirde en dıştaki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="e94fe-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="e94fe-113">GetChain yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="e94fe-114">Icordebugchain gösteren bir işaretçi bu alır `ICorDebugFrame` bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e94fe-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="e94fe-115">GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="e94fe-116">Bu yığın çerçevesi ile ilişkili Icordebugcode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e94fe-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="e94fe-117">GetFunction yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="e94fe-118">Bu yığın çerçevesi ile ilişkili kodunu içerir ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e94fe-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="e94fe-119">GetFunctionToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="e94fe-120">Bu yığın çerçevesi ile ilişkili kodunu içerir işlevi için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="e94fe-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="e94fe-121">GetStackRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="e94fe-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="e94fe-122">Bu tarafından temsil edilen yığın çerçevesi mutlak bir adres aralığını alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="e94fe-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e94fe-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e94fe-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e94fe-124">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e94fe-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e94fe-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e94fe-125">Requirements</span></span>  
 <span data-ttu-id="e94fe-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e94fe-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e94fe-127">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e94fe-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e94fe-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e94fe-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e94fe-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e94fe-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94fe-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e94fe-130">See Also</span></span>  
 [<span data-ttu-id="e94fe-131">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e94fe-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
