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
ms.openlocfilehash: 1ea0274adc12f3a99df0422bfc0b5180f0ef5596
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131385"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="e30fb-102">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e30fb-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="e30fb-103">Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e30fb-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e30fb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e30fb-104">Methods</span></span>  
  
|<span data-ttu-id="e30fb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e30fb-105">Method</span></span>|<span data-ttu-id="e30fb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e30fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e30fb-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30fb-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="e30fb-108">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e30fb-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="e30fb-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30fb-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="e30fb-110">Şu anda bu `ICorDebugRegisterSet` yazmaçların kullanılabildiğini belirten bir bit maskesi alır.</span><span class="sxs-lookup"><span data-stu-id="e30fb-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="e30fb-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30fb-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="e30fb-112">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="e30fb-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="e30fb-113">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30fb-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="e30fb-114">.NET Framework sürüm 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e30fb-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="e30fb-115">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30fb-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="e30fb-116">.NET Framework 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e30fb-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e30fb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e30fb-117">Remarks</span></span>  
 <span data-ttu-id="e30fb-118">`ICorDebugRegisterSet` arabirimi yalnızca 32 bitlik kayıtları destekler.</span><span class="sxs-lookup"><span data-stu-id="e30fb-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="e30fb-119">Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) arabirimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e30fb-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e30fb-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e30fb-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e30fb-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e30fb-121">Requirements</span></span>  
 <span data-ttu-id="e30fb-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e30fb-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e30fb-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e30fb-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e30fb-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e30fb-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e30fb-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e30fb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30fb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e30fb-126">See also</span></span>

- [<span data-ttu-id="e30fb-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e30fb-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e30fb-128">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e30fb-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
