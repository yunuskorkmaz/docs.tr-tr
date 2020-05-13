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
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209636"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="7790a-102">ICorDebugFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7790a-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="7790a-103">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7790a-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7790a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7790a-104">Methods</span></span>  
  
|<span data-ttu-id="7790a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7790a-105">Method</span></span>|<span data-ttu-id="7790a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7790a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7790a-107">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="7790a-108">Bu işleme göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="7790a-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="7790a-109">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="7790a-110">`ICorDebugFrame`Geçerli zincirde bu karenin çağırdığı bir işaretçisini alır veya zincirde en içteki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7790a-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="7790a-111">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="7790a-112">`ICorDebugFrame`Bu çerçeveyi çağıran geçerli zincirde ' a bir işaretçi alır veya zincirde en dıştaki çerçevese null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7790a-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="7790a-113">GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="7790a-114">Bir parçası olan ıcordebugzincirine yönelik bir işaretçi alır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="7790a-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="7790a-115">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="7790a-116">Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="7790a-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="7790a-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="7790a-118">Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="7790a-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="7790a-119">GetFunctionToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="7790a-120">Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="7790a-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="7790a-121">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7790a-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="7790a-122">Bu tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="7790a-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7790a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7790a-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7790a-124">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7790a-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7790a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7790a-125">Requirements</span></span>  
 <span data-ttu-id="7790a-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7790a-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7790a-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7790a-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7790a-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7790a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7790a-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7790a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7790a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7790a-130">See also</span></span>

- [<span data-ttu-id="7790a-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7790a-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
