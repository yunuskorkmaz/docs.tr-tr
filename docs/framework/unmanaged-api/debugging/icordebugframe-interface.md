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
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937001"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="d5d31-102">ICorDebugFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5d31-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="d5d31-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d5d31-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5d31-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d5d31-104">Methods</span></span>  
  
|<span data-ttu-id="d5d31-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d5d31-105">Method</span></span>|<span data-ttu-id="d5d31-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5d31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5d31-107">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="d5d31-108">Bu `ICorDebugFrame`işleme göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır.</span><span class="sxs-lookup"><span data-stu-id="d5d31-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="d5d31-109">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="d5d31-110">Geçerli zincirde bu karenin çağırdığı `ICorDebugFrame` bir işaretçisini alır veya zincirde en içteki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5d31-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="d5d31-111">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="d5d31-112">Bu çerçeveyi çağıran geçerli zincirde `ICorDebugFrame` ' a bir işaretçi alır veya zincirde en dıştaki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5d31-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="d5d31-113">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="d5d31-114">Bir parçası `ICorDebugFrame` olan ıcordebugzincirine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d5d31-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="d5d31-115">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="d5d31-116">Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d5d31-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="d5d31-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="d5d31-118">Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d5d31-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="d5d31-119">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="d5d31-120">Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="d5d31-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="d5d31-121">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d31-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="d5d31-122">Bu `ICorDebugFrame`tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="d5d31-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5d31-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5d31-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d31-124">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d5d31-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d31-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5d31-125">Requirements</span></span>  
 <span data-ttu-id="d5d31-126">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d31-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d31-127">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5d31-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5d31-128">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5d31-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5d31-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d31-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d31-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d31-130">See also</span></span>

- [<span data-ttu-id="d5d31-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5d31-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
