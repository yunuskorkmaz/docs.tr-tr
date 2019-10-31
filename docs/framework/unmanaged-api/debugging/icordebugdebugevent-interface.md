---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: ea42faa4001fa880354690df1551de3be767e683
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137034"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="17a9d-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17a9d-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="17a9d-103">Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17a9d-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17a9d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="17a9d-104">Methods</span></span>  
  
|<span data-ttu-id="17a9d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="17a9d-105">Method</span></span>|<span data-ttu-id="17a9d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17a9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17a9d-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17a9d-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="17a9d-108">Bu `ICorDebugDebugEvent` nesnesinin ne tür bir olayın temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17a9d-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="17a9d-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17a9d-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="17a9d-110">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="17a9d-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17a9d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17a9d-111">Remarks</span></span>  
 <span data-ttu-id="17a9d-112">Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:</span><span class="sxs-lookup"><span data-stu-id="17a9d-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="17a9d-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="17a9d-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="17a9d-114">Icordebugmoduledebugevent</span><span class="sxs-lookup"><span data-stu-id="17a9d-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="17a9d-115">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="17a9d-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="17a9d-116">Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.</span><span class="sxs-lookup"><span data-stu-id="17a9d-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17a9d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17a9d-117">Requirements</span></span>  
 <span data-ttu-id="17a9d-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17a9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17a9d-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="17a9d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17a9d-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="17a9d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17a9d-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17a9d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a9d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17a9d-122">See also</span></span>

- [<span data-ttu-id="17a9d-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="17a9d-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="17a9d-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="17a9d-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
