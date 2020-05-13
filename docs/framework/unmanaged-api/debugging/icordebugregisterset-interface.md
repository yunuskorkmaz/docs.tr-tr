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
ms.openlocfilehash: 7c60fa775b82372b50d1eb3891f107b97df3e73a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378267"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="c05d4-102">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c05d4-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="c05d4-103">Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c05d4-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c05d4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c05d4-104">Methods</span></span>  
  
|<span data-ttu-id="c05d4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c05d4-105">Method</span></span>|<span data-ttu-id="c05d4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c05d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c05d4-107">GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="c05d4-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="c05d4-108">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c05d4-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="c05d4-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05d4-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="c05d4-110">Bu, içindeki yazmaçların Şu anda kullanılabilir olduğunu gösteren bir bit maskesi alır `ICorDebugRegisterSet` .</span><span class="sxs-lookup"><span data-stu-id="c05d4-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="c05d4-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05d4-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="c05d4-112">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="c05d4-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="c05d4-113">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05d4-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="c05d4-114">.NET Framework sürüm 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="c05d4-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="c05d4-115">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05d4-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="c05d4-116">.NET Framework 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="c05d4-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c05d4-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c05d4-117">Remarks</span></span>  
 <span data-ttu-id="c05d4-118">`ICorDebugRegisterSet`Arabirim yalnızca 32 bitlik kayıtları destekler.</span><span class="sxs-lookup"><span data-stu-id="c05d4-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="c05d4-119">Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) arabirimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c05d4-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c05d4-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c05d4-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05d4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c05d4-121">Requirements</span></span>  
 <span data-ttu-id="c05d4-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05d4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05d4-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c05d4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c05d4-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c05d4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c05d4-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05d4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05d4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c05d4-126">See also</span></span>

- [<span data-ttu-id="c05d4-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c05d4-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c05d4-128">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c05d4-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
