---
title: ICorDebugDebugEvent Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4422b165f06b60dedff95fc3de58e5627db7fac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="fb97e-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb97e-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="fb97e-103">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olayları türetilir.</span><span class="sxs-lookup"><span data-stu-id="fb97e-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb97e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fb97e-104">Methods</span></span>  
  
|<span data-ttu-id="fb97e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fb97e-105">Method</span></span>|<span data-ttu-id="fb97e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb97e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb97e-107">GetEventKind yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb97e-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="fb97e-108">Bu olay türlerini gösterir `ICorDebugDebugEvent` nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb97e-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="fb97e-109">GetThread yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb97e-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="fb97e-110">Olayın oluştuğu iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="fb97e-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb97e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb97e-111">Remarks</span></span>  
 <span data-ttu-id="fb97e-112">Aşağıdaki arabirimleri türetilmiş `ICorDebugDebugEvent` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="fb97e-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="fb97e-113">Icordebugexceptiondebugevent</span><span class="sxs-lookup"><span data-stu-id="fb97e-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="fb97e-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="fb97e-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="fb97e-115">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb97e-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="fb97e-116">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="fb97e-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb97e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb97e-117">Requirements</span></span>  
 <span data-ttu-id="fb97e-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb97e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb97e-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb97e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb97e-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb97e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb97e-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb97e-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb97e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb97e-122">See Also</span></span>  
 [<span data-ttu-id="fb97e-123">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb97e-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fb97e-124">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fb97e-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
