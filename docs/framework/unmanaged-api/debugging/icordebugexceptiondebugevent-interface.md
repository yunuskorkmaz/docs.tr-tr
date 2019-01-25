---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7d2407e56b029d22d25a4836f4def1c55f979ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550532"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="7a492-102">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a492-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="7a492-103">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) özel durum olaylarının desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="7a492-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a492-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7a492-104">Methods</span></span>  
  
|<span data-ttu-id="7a492-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7a492-105">Method</span></span>|<span data-ttu-id="7a492-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a492-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a492-107">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a492-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="7a492-108">Bir özel durum olup olmadığını belirten bayrağı alır geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a492-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="7a492-109">GetNativeIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a492-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="7a492-110">Bu özel durum hata ayıklama olayı için yerel arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7a492-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="7a492-111">GetStackPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a492-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="7a492-112">Bu özel durum hata ayıklama olayı için yığın işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7a492-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a492-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a492-113">Remarks</span></span>  
 <span data-ttu-id="7a492-114">`ICorDebugExceptionDebugEvent` Arabirimi aşağıdaki olay türlerine göre uygulanır:</span><span class="sxs-lookup"><span data-stu-id="7a492-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="7a492-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7a492-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7a492-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7a492-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7a492-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="7a492-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7a492-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="7a492-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="7a492-119">Arabirimi yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a492-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="7a492-120">Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="7a492-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a492-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a492-121">Requirements</span></span>  
 <span data-ttu-id="7a492-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a492-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a492-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a492-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a492-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a492-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a492-125">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a492-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a492-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a492-126">See also</span></span>
- [<span data-ttu-id="7a492-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a492-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7a492-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7a492-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
