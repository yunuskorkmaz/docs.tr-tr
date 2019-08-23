---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522bccb4a424da620063995d02ae15d09ecbf2fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929874"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="2e12b-102">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e12b-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="2e12b-103">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="2e12b-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e12b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2e12b-104">Methods</span></span>  
  
|<span data-ttu-id="2e12b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2e12b-105">Method</span></span>|<span data-ttu-id="2e12b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e12b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e12b-107">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e12b-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="2e12b-108">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="2e12b-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="2e12b-109">GetNativeIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e12b-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="2e12b-110">Bu özel durum ayıklama olayı için yerel arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="2e12b-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="2e12b-111">GetStackPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e12b-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="2e12b-112">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="2e12b-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e12b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e12b-113">Remarks</span></span>  
 <span data-ttu-id="2e12b-114">`ICorDebugExceptionDebugEvent` Arabirim aşağıdaki olay türleri tarafından uygulanır:</span><span class="sxs-lookup"><span data-stu-id="2e12b-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="2e12b-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2e12b-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="2e12b-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2e12b-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="2e12b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="2e12b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="2e12b-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="2e12b-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="2e12b-119">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e12b-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="2e12b-120">.NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="2e12b-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e12b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e12b-121">Requirements</span></span>  
 <span data-ttu-id="2e12b-122">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e12b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e12b-123">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e12b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e12b-124">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e12b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e12b-125">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e12b-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e12b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e12b-126">See also</span></span>

- [<span data-ttu-id="2e12b-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2e12b-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2e12b-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2e12b-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
