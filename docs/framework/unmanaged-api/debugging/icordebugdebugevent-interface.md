---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110194"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="45042-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45042-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="45042-103">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir.</span><span class="sxs-lookup"><span data-stu-id="45042-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45042-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="45042-104">Methods</span></span>  
  
|<span data-ttu-id="45042-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="45042-105">Method</span></span>|<span data-ttu-id="45042-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45042-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45042-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45042-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="45042-108">Bu olay türünü gösterir `ICorDebugDebugEvent` nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45042-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="45042-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45042-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="45042-110">Olayın gerçekleştiği iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="45042-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45042-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45042-111">Remarks</span></span>  
 <span data-ttu-id="45042-112">Aşağıdaki arabirimlerinden türetilmiştir `ICorDebugDebugEvent` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="45042-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="45042-113">Icordebugexceptiondebugevent</span><span class="sxs-lookup"><span data-stu-id="45042-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="45042-114">Icordebugmoduledebugevent</span><span class="sxs-lookup"><span data-stu-id="45042-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="45042-115">Arabirimi yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45042-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="45042-116">Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="45042-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45042-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45042-117">Requirements</span></span>  
 <span data-ttu-id="45042-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45042-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45042-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45042-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45042-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45042-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="45042-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="45042-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45042-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45042-122">See also</span></span>

- [<span data-ttu-id="45042-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="45042-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="45042-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="45042-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
