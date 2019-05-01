---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989176"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="dc5d0-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5d0-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="dc5d0-103">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir.</span><span class="sxs-lookup"><span data-stu-id="dc5d0-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc5d0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dc5d0-104">Methods</span></span>  
  
|<span data-ttu-id="dc5d0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dc5d0-105">Method</span></span>|<span data-ttu-id="dc5d0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc5d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc5d0-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5d0-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="dc5d0-108">Bu olay türünü gösterir `ICorDebugDebugEvent` nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dc5d0-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="dc5d0-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5d0-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="dc5d0-110">Olayın gerçekleştiği iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="dc5d0-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc5d0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc5d0-111">Remarks</span></span>  
 <span data-ttu-id="dc5d0-112">Aşağıdaki arabirimlerinden türetilmiştir `ICorDebugDebugEvent` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="dc5d0-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="dc5d0-113">Icordebugexceptiondebugevent</span><span class="sxs-lookup"><span data-stu-id="dc5d0-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="dc5d0-114">Icordebugmoduledebugevent</span><span class="sxs-lookup"><span data-stu-id="dc5d0-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="dc5d0-115">Arabirimi yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc5d0-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="dc5d0-116">Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="dc5d0-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc5d0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc5d0-117">Requirements</span></span>  
 <span data-ttu-id="dc5d0-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc5d0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc5d0-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc5d0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc5d0-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc5d0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc5d0-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc5d0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5d0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5d0-122">See also</span></span>

- [<span data-ttu-id="dc5d0-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc5d0-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dc5d0-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dc5d0-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
