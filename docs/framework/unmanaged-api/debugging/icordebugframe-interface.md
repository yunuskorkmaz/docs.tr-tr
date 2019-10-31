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
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124070"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="62280-102">ICorDebugFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62280-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="62280-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62280-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62280-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="62280-104">Methods</span></span>  
  
|<span data-ttu-id="62280-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="62280-105">Method</span></span>|<span data-ttu-id="62280-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62280-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62280-107">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="62280-108">Bu `ICorDebugFrame`göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır.</span><span class="sxs-lookup"><span data-stu-id="62280-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="62280-109">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="62280-110">Geçerli zincirde bu karenin çağırdığı `ICorDebugFrame` bir işaretçi alır veya bu, zincirdeki en içteki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="62280-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="62280-111">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="62280-112">Bu çerçeveyi çağıran geçerli zincirde `ICorDebugFrame` bir işaretçi alır ya da zincirde en dıştaki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="62280-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="62280-113">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="62280-114">Bu `ICorDebugFrame` bir parçası olan ıcordebugzincirine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="62280-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="62280-115">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="62280-116">Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="62280-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="62280-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="62280-118">Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="62280-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="62280-119">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="62280-120">Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="62280-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="62280-121">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62280-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="62280-122">Bu `ICorDebugFrame`temsil eden yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="62280-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62280-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62280-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62280-124">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="62280-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62280-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62280-125">Requirements</span></span>  
 <span data-ttu-id="62280-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62280-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62280-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62280-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62280-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62280-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62280-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62280-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62280-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62280-130">See also</span></span>

- [<span data-ttu-id="62280-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="62280-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
