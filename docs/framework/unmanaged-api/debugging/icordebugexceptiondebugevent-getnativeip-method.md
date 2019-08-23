---
title: 'Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa1a160bb316831540f68713647dbdc4b0f6895
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951848"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="a5aae-102">Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5aae-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="a5aae-103">Bu özel durum ayıklama olayı için yerel yönerge işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="a5aae-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5aae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5aae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5aae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5aae-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="a5aae-106">dışı Bu özel durum ayıklama olayı için yönerge işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5aae-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="a5aae-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a5aae-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5aae-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5aae-108">Remarks</span></span>  
 <span data-ttu-id="a5aae-109">Bu yönerge işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a5aae-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a5aae-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="a5aae-110">Event type</span></span>|<span data-ttu-id="a5aae-111">`pStackPointer` Değerin anlamı</span><span class="sxs-lookup"><span data-stu-id="a5aae-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="a5aae-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a5aae-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="a5aae-113">Hatalı yönergenin adresi.</span><span class="sxs-lookup"><span data-stu-id="a5aae-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="a5aae-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a5aae-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="a5aae-115">Bir özel durum ortaya çıkarılmadığını yürütmenin sürdürüleceği [Getstackpointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçeve içindeki kod adresidir.</span><span class="sxs-lookup"><span data-stu-id="a5aae-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="a5aae-116">Özel durum, bir `try/catch/finally` yan tümcenin catch bloğu gibi farklı kodların bu çerçevede yürütülmesi olabilir veya neden olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aae-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="a5aae-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="a5aae-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="a5aae-118">`catch` İşleyici yürütmenin [getstackpointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçevede başlayacağı kod adresi.</span><span class="sxs-lookup"><span data-stu-id="a5aae-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="a5aae-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="a5aae-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="a5aae-120">`pIP`0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="a5aae-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="a5aae-121">Olay türü [ıcordebugdebugger gevent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aae-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5aae-122">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aae-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5aae-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5aae-123">Requirements</span></span>  
 <span data-ttu-id="a5aae-124">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5aae-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5aae-125">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5aae-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5aae-126">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5aae-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5aae-127">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5aae-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5aae-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5aae-128">See also</span></span>

- [<span data-ttu-id="a5aae-129">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5aae-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="a5aae-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5aae-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
