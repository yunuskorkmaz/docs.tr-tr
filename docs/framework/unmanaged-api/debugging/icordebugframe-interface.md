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
ms.workload: dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="002ee-102">Icordebugframe Interface1</span><span class="sxs-lookup"><span data-stu-id="002ee-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="002ee-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="002ee-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="002ee-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="002ee-104">Methods</span></span>  
  
|<span data-ttu-id="002ee-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="002ee-105">Method</span></span>|<span data-ttu-id="002ee-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="002ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="002ee-107">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="002ee-108">Bu göreli sürüm işlemlerini gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="002ee-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="002ee-109">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="002ee-110">Bir işaretçi alır `ICorDebugFrame` bu çerçeve olarak adlandırılan veya bu döndürür null ise zincirde en içteki çerçeve geçerli zincirindeki.</span><span class="sxs-lookup"><span data-stu-id="002ee-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="002ee-111">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="002ee-112">Bir işaretçi alır `ICorDebugFrame` geçerli zincirde bu çerçeve denilen ya da bu döndürür null ise zincirde en dıştaki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="002ee-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="002ee-113">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="002ee-114">Icordebugchain gösteren bir işaretçi bu alır `ICorDebugFrame` bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="002ee-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="002ee-115">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="002ee-116">Bu yığın çerçevesi ile ilişkili Icordebugcode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="002ee-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="002ee-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="002ee-118">Bu yığın çerçevesi ile ilişkili kodunu içerir ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="002ee-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="002ee-119">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="002ee-120">Bu yığın çerçevesi ile ilişkili kodunu içerir işlevi için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="002ee-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="002ee-121">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002ee-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="002ee-122">Bu tarafından temsil edilen yığın çerçevesi mutlak bir adres aralığını alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="002ee-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="002ee-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="002ee-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="002ee-124">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="002ee-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002ee-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="002ee-125">Requirements</span></span>  
 <span data-ttu-id="002ee-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002ee-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002ee-127">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="002ee-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002ee-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="002ee-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002ee-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002ee-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002ee-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="002ee-130">See Also</span></span>  
 [<span data-ttu-id="002ee-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="002ee-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
