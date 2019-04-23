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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188714"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="51106-102">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51106-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="51106-103">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="51106-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51106-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="51106-104">Methods</span></span>  
  
|<span data-ttu-id="51106-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="51106-105">Method</span></span>|<span data-ttu-id="51106-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51106-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51106-107">GetPlatform Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51106-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="51106-108">İşlemci mimarisi ve hedef işlem üzerinde çalıştığı işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="51106-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="51106-109">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51106-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="51106-110">Belirtilen adres'ten itibaren bitişik bellek bloğunu alır ve sağlanan arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="51106-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="51106-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51106-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="51106-112">Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını ister.</span><span class="sxs-lookup"><span data-stu-id="51106-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51106-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51106-113">Remarks</span></span>  
 <span data-ttu-id="51106-114">`ICorDebugDataTarget` ve metotlarını şu özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="51106-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="51106-115">Hata ayıklama hizmetlerini, bellek ve diğer verileri hedef işlemde erişmek için bu arabirimdeki yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="51106-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="51106-116">Hata ayıklayıcı istemcisi bu arabirimi belirli hedef (örneğin, canlı bir işlem ya da bir bellek dökümü) için uygun şekilde uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="51106-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="51106-117">`ICorDebugDataTarget` Yöntemleri çağrılacak yalnızca diğer uygulanmış olan yöntemlerle içinde `ICorDebug*` arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="51106-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="51106-118">Bu, hata ayıklayıcı istemcisi olan denetim üzerinde hangi iş parçacığı üzerinde ve çağrılan sağlar.</span><span class="sxs-lookup"><span data-stu-id="51106-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="51106-119">`ICorDebugDataTarget` Uygulama hedef hakkında güncel bilgiler her zaman döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="51106-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="51106-120">Hedef işlem durdurulması ve herhangi bir şekilde değişmemiş `ICorDebug*` arabirimleri (ve bu nedenle `ICorDebugDataTarget` yöntemleri) adı verilir.</span><span class="sxs-lookup"><span data-stu-id="51106-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="51106-121">Hedef canlı bir işlem ve durum değişikliklerini ise [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi olan yeniden değiştirme Icordebugprocess örneği sağlamak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="51106-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51106-122">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="51106-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51106-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51106-123">Requirements</span></span>  
 <span data-ttu-id="51106-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51106-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51106-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51106-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51106-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51106-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51106-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51106-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51106-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51106-128">See also</span></span>

- [<span data-ttu-id="51106-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51106-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="51106-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="51106-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
