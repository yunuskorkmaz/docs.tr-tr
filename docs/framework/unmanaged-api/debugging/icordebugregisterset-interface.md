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
ms.openlocfilehash: 7b0a5d80d984a3c696b178c4d8c936bd47354945
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135245"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="857d5-102">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="857d5-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="857d5-103">Şu anda kod yürüttüğünü bilgisayarda bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="857d5-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="857d5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="857d5-104">Methods</span></span>  
  
|<span data-ttu-id="857d5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="857d5-105">Method</span></span>|<span data-ttu-id="857d5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="857d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="857d5-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="857d5-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="857d5-108">Her kaydın değerini alır (şu anda kod yürüttüğünü bilgisayarda) bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="857d5-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="857d5-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="857d5-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="857d5-110">Alır bir bit maskesi bu kayıtları belirten `ICorDebugRegisterSet` şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="857d5-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="857d5-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="857d5-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="857d5-112">Geçerli iş parçacığı bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="857d5-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="857d5-113">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="857d5-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="857d5-114">.NET Framework sürüm 2.0 uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="857d5-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="857d5-115">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="857d5-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="857d5-116">.NET Framework 2.0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="857d5-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="857d5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="857d5-117">Remarks</span></span>  
 <span data-ttu-id="857d5-118">`ICorDebugRegisterSet` Arabirimi yalnızca 32-bit kayıtlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="857d5-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="857d5-119">Kullanım [Icordebugregisterset2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) gerektiren ek kayıtlar gibi platformlardaki IA-64 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="857d5-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="857d5-120">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="857d5-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="857d5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="857d5-121">Requirements</span></span>  
 <span data-ttu-id="857d5-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="857d5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="857d5-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="857d5-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="857d5-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="857d5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="857d5-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="857d5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857d5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="857d5-126">See also</span></span>

- [<span data-ttu-id="857d5-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="857d5-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="857d5-128">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="857d5-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
