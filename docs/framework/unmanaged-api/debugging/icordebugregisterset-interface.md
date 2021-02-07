---
description: ': ICorDebugRegisterSet arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7d888e9e395e9f5fa88c6a6d96b2b8e3171ef4ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690788"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="a096e-103">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a096e-103">ICorDebugRegisterSet Interface</span></span>

<span data-ttu-id="a096e-104">Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a096e-104">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a096e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a096e-105">Methods</span></span>  
  
|<span data-ttu-id="a096e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a096e-106">Method</span></span>|<span data-ttu-id="a096e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a096e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a096e-108">GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="a096e-108">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="a096e-109">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a096e-109">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="a096e-110">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a096e-110">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="a096e-111">Bu, içindeki yazmaçların Şu anda kullanılabilir olduğunu gösteren bir bit maskesi alır `ICorDebugRegisterSet` .</span><span class="sxs-lookup"><span data-stu-id="a096e-111">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="a096e-112">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a096e-112">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="a096e-113">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="a096e-113">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="a096e-114">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a096e-114">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="a096e-115">.NET Framework sürüm 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a096e-115">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="a096e-116">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a096e-116">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="a096e-117">.NET Framework 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a096e-117">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a096e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a096e-118">Remarks</span></span>  

 <span data-ttu-id="a096e-119">`ICorDebugRegisterSet`Arabirim yalnızca 32 bitlik kayıtları destekler.</span><span class="sxs-lookup"><span data-stu-id="a096e-119">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="a096e-120">Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) arabirimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a096e-120">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a096e-121">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a096e-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a096e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a096e-122">Requirements</span></span>  

 <span data-ttu-id="a096e-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a096e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a096e-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a096e-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a096e-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a096e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a096e-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a096e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a096e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a096e-127">See also</span></span>

- [<span data-ttu-id="a096e-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a096e-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a096e-129">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a096e-129">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
