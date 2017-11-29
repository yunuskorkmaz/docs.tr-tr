---
title: "ICorDebugExceptionDebugEvent::GetNativeIP yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 616f0a9787220aba0cc4d460c80b856076e1e437
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="f0c05-102">ICorDebugExceptionDebugEvent::GetNativeIP yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0c05-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="f0c05-103">Yerel yönerge işaretçisi için bu özel durum hata ayıklama olayı alır.</span><span class="sxs-lookup"><span data-stu-id="f0c05-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0c05-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0c05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0c05-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="f0c05-106">[out] Bu özel durumun yönerge işaretçisi gösteren bir işaretçi olay hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="f0c05-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="f0c05-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f0c05-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0c05-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0c05-108">Remarks</span></span>  
 <span data-ttu-id="f0c05-109">Bu yönerge işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="f0c05-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f0c05-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="f0c05-110">Event type</span></span>|<span data-ttu-id="f0c05-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="f0c05-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="f0c05-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f0c05-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0c05-113">Hataya neden olan yönerge adresi.</span><span class="sxs-lookup"><span data-stu-id="f0c05-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="f0c05-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f0c05-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0c05-115">Kod adresi çerçevesinde gösterilen tarafından [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) burada yürütme devam herhangi bir özel durumu gerçekleşti, yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0c05-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="f0c05-116">Özel durum olabilir veya catch bloğu gibi farklı bir kod neden olmaz bir `try/catch/finally` Bu çerçevede yürütülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f0c05-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="f0c05-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="f0c05-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0c05-118">Kodu nereye adres `catch` işleyici yürütme belirttiği çerçevesinde başlayacak [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0c05-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="f0c05-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="f0c05-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0c05-120">`pIP`0'dır.</span><span class="sxs-lookup"><span data-stu-id="f0c05-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="f0c05-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0c05-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0c05-122">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0c05-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c05-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0c05-123">Requirements</span></span>  
 <span data-ttu-id="f0c05-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c05-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c05-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0c05-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0c05-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0c05-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0c05-127">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c05-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c05-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0c05-128">See Also</span></span>  
 [<span data-ttu-id="f0c05-129">Icordebugexceptiondebugevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0c05-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="f0c05-130">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0c05-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
