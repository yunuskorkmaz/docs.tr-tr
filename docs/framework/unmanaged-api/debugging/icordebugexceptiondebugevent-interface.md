---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 985edaa14510b7ca03399ae17cf1d89f28fd04c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084649"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="2540b-102">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2540b-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="2540b-103">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="2540b-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2540b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2540b-104">Methods</span></span>  
  
|<span data-ttu-id="2540b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2540b-105">Method</span></span>|<span data-ttu-id="2540b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2540b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2540b-107">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2540b-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="2540b-108">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="2540b-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="2540b-109">GetNativeIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2540b-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="2540b-110">Bu özel durum ayıklama olayı için yerel arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="2540b-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="2540b-111">GetStackPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2540b-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="2540b-112">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="2540b-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2540b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2540b-113">Remarks</span></span>  
 <span data-ttu-id="2540b-114">`ICorDebugExceptionDebugEvent` arabirimi aşağıdaki olay türleri tarafından uygulanır:</span><span class="sxs-lookup"><span data-stu-id="2540b-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="2540b-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2540b-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="2540b-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2540b-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="2540b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="2540b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="2540b-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="2540b-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="2540b-119">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2540b-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="2540b-120">Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.</span><span class="sxs-lookup"><span data-stu-id="2540b-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2540b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2540b-121">Requirements</span></span>  
 <span data-ttu-id="2540b-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2540b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2540b-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2540b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2540b-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2540b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2540b-125">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2540b-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2540b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2540b-126">See also</span></span>

- [<span data-ttu-id="2540b-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2540b-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2540b-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2540b-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
