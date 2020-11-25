---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: d73857bd9d0d5dd9e5eff0c89dcc573ae0d93f0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731884"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="b1660-102">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1660-102">ICorDebugDebugEvent Interface</span></span>

<span data-ttu-id="b1660-103">Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1660-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1660-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b1660-104">Methods</span></span>  
  
|<span data-ttu-id="b1660-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b1660-105">Method</span></span>|<span data-ttu-id="b1660-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1660-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1660-107">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1660-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="b1660-108">Bu nesnenin ne tür bir olayın `ICorDebugDebugEvent` temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1660-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="b1660-109">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1660-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="b1660-110">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="b1660-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1660-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1660-111">Remarks</span></span>  

 <span data-ttu-id="b1660-112">Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:</span><span class="sxs-lookup"><span data-stu-id="b1660-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="b1660-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="b1660-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="b1660-114">Icordebugmoduledebugevent</span><span class="sxs-lookup"><span data-stu-id="b1660-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="b1660-115">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1660-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="b1660-116">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="b1660-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1660-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1660-117">Requirements</span></span>  

 <span data-ttu-id="b1660-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1660-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1660-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1660-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1660-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1660-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1660-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1660-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1660-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1660-122">See also</span></span>

- [<span data-ttu-id="b1660-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b1660-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b1660-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b1660-124">Debugging</span></span>](index.md)
