---
title: 'Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788679"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="6aa64-102">Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi</span><span class="sxs-lookup"><span data-stu-id="6aa64-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="6aa64-103">Bu özel durum ayıklama olayı için yerel yönerge işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="6aa64-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6aa64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aa64-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6aa64-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="6aa64-106">dışı Bu özel durum ayıklama olayı için yönerge işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6aa64-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="6aa64-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6aa64-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aa64-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6aa64-108">Remarks</span></span>  
 <span data-ttu-id="6aa64-109">Bu yönerge işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6aa64-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="6aa64-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="6aa64-110">Event type</span></span>|<span data-ttu-id="6aa64-111">`pStackPointer` değerinin anlamı</span><span class="sxs-lookup"><span data-stu-id="6aa64-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="6aa64-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="6aa64-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="6aa64-113">Hatalı yönergenin adresi.</span><span class="sxs-lookup"><span data-stu-id="6aa64-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="6aa64-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="6aa64-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="6aa64-115">Bir özel durum ortaya çıkarılmadığını yürütmenin sürdürüleceği [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçeve içindeki kod adresidir.</span><span class="sxs-lookup"><span data-stu-id="6aa64-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="6aa64-116">Özel durum, `try/catch/finally` yan tümcesinin catch bloğu gibi farklı kodların bu çerçevede yürütülmesi olabilir veya neden olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6aa64-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="6aa64-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="6aa64-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="6aa64-118">`catch` Handler yürütmesinin, [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçevede başlayacağı kod adresi.</span><span class="sxs-lookup"><span data-stu-id="6aa64-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="6aa64-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="6aa64-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="6aa64-120">`pIP` 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="6aa64-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="6aa64-121">Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6aa64-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6aa64-122">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6aa64-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aa64-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6aa64-123">Requirements</span></span>  
 <span data-ttu-id="6aa64-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aa64-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aa64-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6aa64-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aa64-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6aa64-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aa64-127">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aa64-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa64-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aa64-128">See also</span></span>

- [<span data-ttu-id="6aa64-129">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6aa64-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="6aa64-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6aa64-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
