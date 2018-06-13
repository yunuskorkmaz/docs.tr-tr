---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a2543a9629c60fde2b2f14c11898ba3e9df3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419318"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="8fec9-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fec9-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="8fec9-103">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olayları türetilir.</span><span class="sxs-lookup"><span data-stu-id="8fec9-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fec9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8fec9-104">Methods</span></span>  
  
|<span data-ttu-id="8fec9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8fec9-105">Method</span></span>|<span data-ttu-id="8fec9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fec9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8fec9-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fec9-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="8fec9-108">Bu olay türlerini gösterir `ICorDebugDebugEvent` nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8fec9-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="8fec9-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fec9-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="8fec9-110">Olayın oluştuğu iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="8fec9-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fec9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fec9-111">Remarks</span></span>  
 <span data-ttu-id="8fec9-112">Aşağıdaki arabirimleri türetilmiş `ICorDebugDebugEvent` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="8fec9-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="8fec9-113">Icordebugexceptiondebugevent</span><span class="sxs-lookup"><span data-stu-id="8fec9-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="8fec9-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8fec9-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="8fec9-115">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fec9-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="8fec9-116">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="8fec9-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fec9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fec9-117">Requirements</span></span>  
 <span data-ttu-id="8fec9-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fec9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fec9-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fec9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fec9-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fec9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fec9-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fec9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fec9-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8fec9-122">See Also</span></span>  
 [<span data-ttu-id="8fec9-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fec9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8fec9-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8fec9-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
