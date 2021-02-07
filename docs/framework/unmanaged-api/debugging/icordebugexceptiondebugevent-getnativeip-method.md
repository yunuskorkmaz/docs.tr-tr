---
description: ': Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 89bda36efc59e2462634c3d8a3a5835c9d4b3354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693466"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="513d6-103">Icordebugexceptiondebugger gevent:: Getnativeıp yöntemi</span><span class="sxs-lookup"><span data-stu-id="513d6-103">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>

<span data-ttu-id="513d6-104">Bu özel durum ayıklama olayı için yerel yönerge işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="513d6-104">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513d6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="513d6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="513d6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="513d6-106">Parameters</span></span>  

 `pIP`  
 <span data-ttu-id="513d6-107">dışı Bu özel durum ayıklama olayı için yönerge işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="513d6-107">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="513d6-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="513d6-108">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="513d6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="513d6-109">Remarks</span></span>  

 <span data-ttu-id="513d6-110">Bu yönerge işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="513d6-110">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="513d6-111">Olay türü</span><span class="sxs-lookup"><span data-stu-id="513d6-111">Event type</span></span>|<span data-ttu-id="513d6-112">Değerin anlamı `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="513d6-112">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="513d6-113">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="513d6-113">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="513d6-114">Hatalı yönergenin adresi.</span><span class="sxs-lookup"><span data-stu-id="513d6-114">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="513d6-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="513d6-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="513d6-116">Bir özel durum ortaya çıkarılmadığını yürütmenin sürdürüleceği [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçeve içindeki kod adresidir.</span><span class="sxs-lookup"><span data-stu-id="513d6-116">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="513d6-117">Özel durum, bir yan tümcenin catch bloğu gibi farklı kodların bu çerçevede yürütülmesi olabilir veya neden olmayabilir `try/catch/finally` .</span><span class="sxs-lookup"><span data-stu-id="513d6-117">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="513d6-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="513d6-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="513d6-119">`catch`İşleyici yürütmenin [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi tarafından belirtilen çerçevede başlayacağı kod adresi.</span><span class="sxs-lookup"><span data-stu-id="513d6-119">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="513d6-120">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="513d6-120">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="513d6-121">`pIP` 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="513d6-121">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="513d6-122">Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="513d6-122">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="513d6-123">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="513d6-123">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="513d6-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="513d6-124">Requirements</span></span>  

 <span data-ttu-id="513d6-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="513d6-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="513d6-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="513d6-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="513d6-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="513d6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="513d6-128">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="513d6-128">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513d6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="513d6-129">See also</span></span>

- [<span data-ttu-id="513d6-130">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="513d6-130">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="513d6-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="513d6-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
