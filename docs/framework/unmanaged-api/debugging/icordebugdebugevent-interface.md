---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f838c9c2775023583b6879ea4c4a52727065114
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911259"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="54c9e-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54c9e-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="54c9e-103">Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54c9e-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54c9e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54c9e-104">Methods</span></span>  
  
|<span data-ttu-id="54c9e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="54c9e-105">Method</span></span>|<span data-ttu-id="54c9e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54c9e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54c9e-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54c9e-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="54c9e-108">Bu `ICorDebugDebugEvent` nesnenin ne tür bir olayın temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="54c9e-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="54c9e-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54c9e-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="54c9e-110">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="54c9e-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54c9e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54c9e-111">Remarks</span></span>  
 <span data-ttu-id="54c9e-112">Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:</span><span class="sxs-lookup"><span data-stu-id="54c9e-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="54c9e-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="54c9e-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="54c9e-114">Icordebugmoduledebugevent</span><span class="sxs-lookup"><span data-stu-id="54c9e-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="54c9e-115">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54c9e-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="54c9e-116">.NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="54c9e-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c9e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54c9e-117">Requirements</span></span>  
 <span data-ttu-id="54c9e-118">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c9e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c9e-119">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54c9e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54c9e-120">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="54c9e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54c9e-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c9e-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c9e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54c9e-122">See also</span></span>

- [<span data-ttu-id="54c9e-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54c9e-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="54c9e-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="54c9e-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
