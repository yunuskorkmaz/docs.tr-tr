---
title: ICorDebugRegisterSet Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4b28d60b3a1da32d2d9db84aa92ca4c9bf769aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423201"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="9d3b6-102">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="9d3b6-103">Yazmaçları kod şu anda yürütülmekte bilgisayarda kullanılabilir kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d3b6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d3b6-104">Methods</span></span>  
  
|<span data-ttu-id="9d3b6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d3b6-105">Method</span></span>|<span data-ttu-id="9d3b6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d3b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d3b6-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="9d3b6-108">Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="9d3b6-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="9d3b6-110">Alır bir bit maskesi bu kayıtları belirten `ICorDebugRegisterSet` şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="9d3b6-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="9d3b6-112">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="9d3b6-113">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="9d3b6-114">.NET Framework sürüm 2.0 uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="9d3b6-115">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="9d3b6-116">.NET Framework 2.0 uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d3b6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d3b6-117">Remarks</span></span>  
 <span data-ttu-id="9d3b6-118">`ICorDebugRegisterSet` Arabirimi yalnızca 32-bit kayıtlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="9d3b6-119">Kullanım [Icordebugregisterset2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) platformlarda ek kayıtları gerektiren IA-64 gibi arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d3b6-120">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d3b6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d3b6-121">Requirements</span></span>  
 <span data-ttu-id="9d3b6-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d3b6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d3b6-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d3b6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d3b6-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d3b6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d3b6-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d3b6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3b6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d3b6-126">See Also</span></span>  
 [<span data-ttu-id="9d3b6-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d3b6-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9d3b6-128">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d3b6-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
