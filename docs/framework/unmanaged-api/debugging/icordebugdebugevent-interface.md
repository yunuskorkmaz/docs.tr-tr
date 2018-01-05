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
ms.workload: dotnet
ms.openlocfilehash: 1c4d777d601866ca9600a7e2b88aca8854f32a17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="16cb4-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16cb4-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="16cb4-103">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olayları türetilir.</span><span class="sxs-lookup"><span data-stu-id="16cb4-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16cb4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="16cb4-104">Methods</span></span>  
  
|<span data-ttu-id="16cb4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="16cb4-105">Method</span></span>|<span data-ttu-id="16cb4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16cb4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16cb4-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16cb4-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="16cb4-108">Bu olay türlerini gösterir `ICorDebugDebugEvent` nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="16cb4-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="16cb4-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16cb4-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="16cb4-110">Olayın oluştuğu iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="16cb4-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16cb4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16cb4-111">Remarks</span></span>  
 <span data-ttu-id="16cb4-112">Aşağıdaki arabirimleri türetilmiş `ICorDebugDebugEvent` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="16cb4-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="16cb4-113">Icordebugexceptiondebugevent</span><span class="sxs-lookup"><span data-stu-id="16cb4-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="16cb4-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="16cb4-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="16cb4-115">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16cb4-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="16cb4-116">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="16cb4-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16cb4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16cb4-117">Requirements</span></span>  
 <span data-ttu-id="16cb4-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16cb4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16cb4-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16cb4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16cb4-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16cb4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16cb4-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16cb4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cb4-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16cb4-122">See Also</span></span>  
 [<span data-ttu-id="16cb4-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="16cb4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="16cb4-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="16cb4-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
