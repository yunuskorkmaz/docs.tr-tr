---
title: ICorDebugExceptionDebugEvent::GetNativeIP yöntemi
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2cb505b5a6657ee5c12a8a0a97bff548649a219
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417159"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="27871-102">ICorDebugExceptionDebugEvent::GetNativeIP yöntemi</span><span class="sxs-lookup"><span data-stu-id="27871-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="27871-103">Yerel yönerge işaretçisi için bu özel durum hata ayıklama olayı alır.</span><span class="sxs-lookup"><span data-stu-id="27871-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27871-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27871-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27871-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27871-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="27871-106">[out] Bu özel durumun yönerge işaretçisi gösteren bir işaretçi olay hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="27871-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="27871-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="27871-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27871-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27871-108">Remarks</span></span>  
 <span data-ttu-id="27871-109">Bu yönerge işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="27871-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="27871-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="27871-110">Event type</span></span>|<span data-ttu-id="27871-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="27871-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="27871-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="27871-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="27871-113">Hataya neden olan yönerge adresi.</span><span class="sxs-lookup"><span data-stu-id="27871-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="27871-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="27871-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="27871-115">Kod adresi çerçevesinde gösterilen tarafından [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) burada yürütme devam herhangi bir özel durumu gerçekleşti, yöntemi.</span><span class="sxs-lookup"><span data-stu-id="27871-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="27871-116">Özel durum olabilir veya catch bloğu gibi farklı bir kod neden olmaz bir `try/catch/finally` Bu çerçevede yürütülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="27871-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="27871-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="27871-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="27871-118">Kodu nereye adres `catch` işleyici yürütme belirttiği çerçevesinde başlayacak [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="27871-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="27871-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="27871-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="27871-120">`pIP` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="27871-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="27871-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="27871-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27871-122">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27871-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27871-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27871-123">Requirements</span></span>  
 <span data-ttu-id="27871-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27871-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27871-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27871-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27871-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27871-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27871-127">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27871-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27871-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27871-128">See Also</span></span>  
 [<span data-ttu-id="27871-129">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27871-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="27871-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27871-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
