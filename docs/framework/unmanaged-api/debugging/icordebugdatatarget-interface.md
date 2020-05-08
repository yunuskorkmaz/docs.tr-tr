---
title: ICorDebugDataTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 54272dd18a12715bab58ec1b1a4c1dc00e4bf12b
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976531"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="9632f-102">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9632f-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="9632f-103">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="9632f-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9632f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9632f-104">Methods</span></span>  
  
|<span data-ttu-id="9632f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9632f-105">Method</span></span>|<span data-ttu-id="9632f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9632f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9632f-107">GetPlatform Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9632f-107">GetPlatform Method</span></span>](icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="9632f-108">Hedef işlemin çalıştığı işlemci mimarisi ve işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9632f-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="9632f-109">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9632f-109">ReadVirtual Method</span></span>](icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="9632f-110">Belirtilen adresten başlayarak bir ardışık bellek bloğunu alır ve sağlanan arabellekte döndürür.</span><span class="sxs-lookup"><span data-stu-id="9632f-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="9632f-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9632f-111">GetThreadContext Method</span></span>](icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="9632f-112">Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını ister.</span><span class="sxs-lookup"><span data-stu-id="9632f-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9632f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9632f-113">Remarks</span></span>  
 <span data-ttu-id="9632f-114">`ICorDebugDataTarget`ve yöntemleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9632f-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="9632f-115">Hata ayıklama Hizmetleri, hedef işlemdeki belleğe ve diğer verilere erişmek için bu arabirimdeki yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="9632f-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="9632f-116">Hata ayıklayıcı istemcisinin, bu arabirimi belirli bir hedefe (örneğin, canlı bir işlem veya bir bellek dökümü) uygun şekilde uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9632f-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="9632f-117">`ICorDebugDataTarget` Yöntemler yalnızca diğer `ICorDebug*` arabirimlerde uygulanan metotların içinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9632f-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="9632f-118">Bu, hata ayıklayıcı istemcisinin üzerinde çağrıldığı iş parçacığı üzerinde denetim sahibi olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9632f-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="9632f-119">`ICorDebugDataTarget` Uygulamanın, hedefle ilgili her zaman güncel bilgileri döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9632f-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="9632f-120">Hedef işlem durdurulmalı ve `ICorDebug*` arabirimler (ve bu nedenle `ICorDebugDataTarget` Yöntemler) çağrıldığında hiçbir şekilde değiştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="9632f-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="9632f-121">Hedef canlı bir işlemdir ve durumu değişirse, bir değiştirme ICorDebugProcess örneği sağlamak için [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yönteminin yeniden çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9632f-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9632f-122">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="9632f-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9632f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9632f-123">Requirements</span></span>  
 <span data-ttu-id="9632f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9632f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9632f-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9632f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9632f-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9632f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9632f-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9632f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9632f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9632f-128">See also</span></span>

- [<span data-ttu-id="9632f-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9632f-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9632f-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9632f-130">Debugging</span></span>](index.md)
