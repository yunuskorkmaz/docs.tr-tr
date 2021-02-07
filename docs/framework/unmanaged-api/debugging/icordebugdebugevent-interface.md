---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugdebugger gevent arabirimi'
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: 5735be22b76e9f74847bb5138c00130f28dbfc96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764313"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="b7e39-103">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7e39-103">ICorDebugDebugEvent Interface</span></span>

<span data-ttu-id="b7e39-104">Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b7e39-104">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7e39-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b7e39-105">Methods</span></span>  
  
|<span data-ttu-id="b7e39-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b7e39-106">Method</span></span>|<span data-ttu-id="b7e39-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7e39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7e39-108">GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7e39-108">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="b7e39-109">Bu nesnenin ne tür bir olayın `ICorDebugDebugEvent` temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7e39-109">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="b7e39-110">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7e39-110">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="b7e39-111">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="b7e39-111">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7e39-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7e39-112">Remarks</span></span>  

 <span data-ttu-id="b7e39-113">Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:</span><span class="sxs-lookup"><span data-stu-id="b7e39-113">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="b7e39-114">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="b7e39-114">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="b7e39-115">Icordebugmoduledebugevent</span><span class="sxs-lookup"><span data-stu-id="b7e39-115">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="b7e39-116">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7e39-116">The interface is available with .NET Native only.</span></span> <span data-ttu-id="b7e39-117">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="b7e39-117">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7e39-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7e39-118">Requirements</span></span>  

 <span data-ttu-id="b7e39-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7e39-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e39-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7e39-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7e39-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b7e39-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7e39-122">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7e39-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e39-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7e39-123">See also</span></span>

- [<span data-ttu-id="b7e39-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b7e39-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b7e39-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b7e39-125">Debugging</span></span>](index.md)
