---
description: ': ICorDebugFrame arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d0fd629672d535f89fe78c178032937443d9dfbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692855"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="04e12-103">ICorDebugFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e12-103">ICorDebugFrame Interface</span></span>

<span data-ttu-id="04e12-104">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04e12-104">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04e12-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="04e12-105">Methods</span></span>  
  
|<span data-ttu-id="04e12-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="04e12-106">Method</span></span>|<span data-ttu-id="04e12-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04e12-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04e12-108">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-108">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="04e12-109">Bu işleme göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="04e12-109">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="04e12-110">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-110">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="04e12-111">`ICorDebugFrame`Geçerli zincirde bu karenin çağırdığı bir işaretçisini alır veya zincirde en içteki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="04e12-111">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="04e12-112">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-112">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="04e12-113">`ICorDebugFrame`Bu çerçeveyi çağıran geçerli zincirde ' a bir işaretçi alır veya zincirde en dıştaki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="04e12-113">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="04e12-114">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-114">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="04e12-115">Bir parçası olan ıcordebugzincirine yönelik bir işaretçi alır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="04e12-115">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="04e12-116">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-116">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="04e12-117">Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="04e12-117">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="04e12-118">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-118">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="04e12-119">Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="04e12-119">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="04e12-120">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-120">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="04e12-121">Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="04e12-121">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="04e12-122">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e12-122">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="04e12-123">Bu tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="04e12-123">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04e12-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04e12-124">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04e12-125">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="04e12-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e12-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04e12-126">Requirements</span></span>  

 <span data-ttu-id="04e12-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e12-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e12-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04e12-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04e12-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="04e12-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04e12-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e12-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e12-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04e12-131">See also</span></span>

- [<span data-ttu-id="04e12-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04e12-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
