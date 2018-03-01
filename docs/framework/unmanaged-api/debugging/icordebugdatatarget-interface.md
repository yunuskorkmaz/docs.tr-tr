---
title: ICorDebugDataTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5d3a3b190cfa606bd4239e24c5defdaff9f4257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="98939-102">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98939-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="98939-103">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="98939-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98939-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98939-104">Methods</span></span>  
  
|<span data-ttu-id="98939-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="98939-105">Method</span></span>|<span data-ttu-id="98939-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98939-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98939-107">GetPlatform Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98939-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="98939-108">İşlemci mimarisi ve hedef işlemin çalıştığı işletim sistemi dahil olmak üzere bu platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="98939-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="98939-109">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98939-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="98939-110">Belirtilen adresten başlayarak bitişik bellek bloğu alır ve sağlanan arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="98939-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="98939-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98939-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="98939-112">Belirtilen iş parçacığı için geçerli iş parçacığının içeriği ister.</span><span class="sxs-lookup"><span data-stu-id="98939-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98939-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98939-113">Remarks</span></span>  
 <span data-ttu-id="98939-114">`ICorDebugDataTarget`ve yöntemlerinden aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="98939-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="98939-115">Hata Ayıklama Hizmetleri, bellek ve diğer verileri hedef işleminde erişmek için bu arabirimde yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="98939-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="98939-116">Hata ayıklayıcı istemci belirli bir hedef (örneğin, canlı bir işlem ya da bir bellek dökümü) için uygun şekilde bu arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="98939-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="98939-117">`ICorDebugDataTarget` Yöntemleri çağrılabilir yalnızca diğer uygulanan yöntemleri içinde `ICorDebug*` arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="98939-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="98939-118">Bu hata ayıklayıcı istemci sahip denetim hangi iş parçacığı üzerinde ve ne zaman çağrılır sağlar.</span><span class="sxs-lookup"><span data-stu-id="98939-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="98939-119">`ICorDebugDataTarget` Uygulama hedef hakkında güncel bilgileri her zaman döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="98939-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="98939-120">Hedef işlem durduruldu ve gerekir sırasında herhangi bir şekilde değiştirilmez `ICorDebug*` arabirimleri (ve bu nedenle `ICorDebugDataTarget` yöntemleri) adı verilir.</span><span class="sxs-lookup"><span data-stu-id="98939-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="98939-121">Hedef, durum değişikliklerini ve canlı bir işlem ise [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi sahip yeniden değiştirme Icordebugprocess örneği sağlamak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="98939-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98939-122">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="98939-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98939-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98939-123">Requirements</span></span>  
 <span data-ttu-id="98939-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98939-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98939-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98939-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98939-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98939-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98939-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98939-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98939-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98939-128">See Also</span></span>  
 [<span data-ttu-id="98939-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98939-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="98939-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="98939-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
