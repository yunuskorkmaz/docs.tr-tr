---
title: ICorDebugFrame Arabirimi
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
ms.openlocfilehash: a15d7f16676b8b9d66f8d1ba7484f3fec5735a44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222574"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="0f3cc-102">ICorDebugFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="0f3cc-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f3cc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f3cc-104">Methods</span></span>  
  
|<span data-ttu-id="0f3cc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f3cc-105">Method</span></span>|<span data-ttu-id="0f3cc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f3cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f3cc-107">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="0f3cc-108">Bu göreli Adımlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="0f3cc-109">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="0f3cc-110">Bir işaretçi alır `ICorDebugFrame` bu çerçeve adlı veya bu null döndürür zincirindeki en içteki çerçeve olan geçerli zincirindeki.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="0f3cc-111">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="0f3cc-112">Bir işaretçi alır `ICorDebugFrame` geçerli zincirinde bu çerçeve adında ya da bu null döndürür zincirindeki en dıştaki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="0f3cc-113">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="0f3cc-114">Bu Icordebugchain bir işaretçi alır `ICorDebugFrame` bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="0f3cc-115">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="0f3cc-116">Bu yığın çerçevesiyle ilgili Icordebugcode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="0f3cc-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="0f3cc-118">Bu yığın çerçevesiyle ilgili kodu içeren ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="0f3cc-119">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="0f3cc-120">Bu yığın çerçevesiyle ilgili kodu içeren işlevi için meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="0f3cc-121">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3cc-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="0f3cc-122">Bu tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f3cc-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f3cc-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f3cc-124">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f3cc-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f3cc-125">Requirements</span></span>  
 <span data-ttu-id="0f3cc-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f3cc-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f3cc-127">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f3cc-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f3cc-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f3cc-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f3cc-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f3cc-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3cc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f3cc-130">See also</span></span>

- [<span data-ttu-id="0f3cc-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f3cc-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
