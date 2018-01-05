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
ms.workload: dotnet
ms.openlocfilehash: 32e75a18645c000562cdd94478c6ef8db41a01a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="5cdbf-102">ICorDebugExceptionDebugEvent::GetNativeIP yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cdbf-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="5cdbf-103">Yerel yönerge işaretçisi için bu özel durum hata ayıklama olayı alır.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cdbf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cdbf-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cdbf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cdbf-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="5cdbf-106">[out] Bu özel durumun yönerge işaretçisi gösteren bir işaretçi olay hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="5cdbf-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cdbf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cdbf-108">Remarks</span></span>  
 <span data-ttu-id="5cdbf-109">Bu yönerge işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="5cdbf-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="5cdbf-110">Event type</span></span>|<span data-ttu-id="5cdbf-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="5cdbf-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="5cdbf-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="5cdbf-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="5cdbf-113">Hataya neden olan yönerge adresi.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="5cdbf-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="5cdbf-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="5cdbf-115">Kod adresi çerçevesinde gösterilen tarafından [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) burada yürütme devam herhangi bir özel durumu gerçekleşti, yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="5cdbf-116">Özel durum olabilir veya catch bloğu gibi farklı bir kod neden olmaz bir `try/catch/finally` Bu çerçevede yürütülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="5cdbf-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="5cdbf-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="5cdbf-118">Kodu nereye adres `catch` işleyici yürütme belirttiği çerçevesinde başlayacak [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="5cdbf-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="5cdbf-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="5cdbf-120">`pIP`0'dır.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="5cdbf-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cdbf-122">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cdbf-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cdbf-123">Requirements</span></span>  
 <span data-ttu-id="5cdbf-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cdbf-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cdbf-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cdbf-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cdbf-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cdbf-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cdbf-127">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cdbf-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdbf-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-128">See Also</span></span>  
 [<span data-ttu-id="5cdbf-129">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cdbf-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="5cdbf-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5cdbf-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
