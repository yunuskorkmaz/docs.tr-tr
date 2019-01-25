---
title: Icordebugframe arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f160612e499ca7bd2185c95aa07a3784c5a4a19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635760"
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="59f2c-102">Icordebugframe arabirimi1</span><span class="sxs-lookup"><span data-stu-id="59f2c-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="59f2c-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59f2c-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59f2c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59f2c-104">Methods</span></span>  
  
|<span data-ttu-id="59f2c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="59f2c-105">Method</span></span>|<span data-ttu-id="59f2c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59f2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59f2c-107">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="59f2c-108">Bu göreli Adımlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="59f2c-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="59f2c-109">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="59f2c-110">Bir işaretçi alır `ICorDebugFrame` bu çerçeve adlı veya bu null döndürür zincirindeki en içteki çerçeve olan geçerli zincirindeki.</span><span class="sxs-lookup"><span data-stu-id="59f2c-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="59f2c-111">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="59f2c-112">Bir işaretçi alır `ICorDebugFrame` geçerli zincirinde bu çerçeve adında ya da bu null döndürür zincirindeki en dıştaki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="59f2c-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="59f2c-113">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="59f2c-114">Bu Icordebugchain bir işaretçi alır `ICorDebugFrame` bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="59f2c-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="59f2c-115">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="59f2c-116">Bu yığın çerçevesiyle ilgili Icordebugcode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="59f2c-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="59f2c-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="59f2c-118">Bu yığın çerçevesiyle ilgili kodu içeren ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="59f2c-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="59f2c-119">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="59f2c-120">Bu yığın çerçevesiyle ilgili kodu içeren işlevi için meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="59f2c-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="59f2c-121">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59f2c-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="59f2c-122">Bu tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="59f2c-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59f2c-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59f2c-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59f2c-124">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="59f2c-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59f2c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59f2c-125">Requirements</span></span>  
 <span data-ttu-id="59f2c-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59f2c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59f2c-127">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59f2c-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59f2c-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59f2c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59f2c-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59f2c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f2c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59f2c-130">See also</span></span>
- [<span data-ttu-id="59f2c-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59f2c-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
