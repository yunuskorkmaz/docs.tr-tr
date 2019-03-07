---
title: ICorDebugExceptionDebugEvent::GetStackPointer yöntemi
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f5ea632ad8a7dd2e24e71742223936b01298f31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485166"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="f3e97-102">ICorDebugExceptionDebugEvent::GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3e97-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="f3e97-103">Bu özel durum hata ayıklama olayı için yığın işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f3e97-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3e97-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3e97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3e97-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="f3e97-106">[out] Olay hata ayıklama bu özel durumun yığın işaretçisinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3e97-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="f3e97-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f3e97-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e97-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3e97-108">Remarks</span></span>  
 <span data-ttu-id="f3e97-109">Bu yığın işaretçisi anlamını, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="f3e97-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f3e97-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="f3e97-110">Event type</span></span>|<span data-ttu-id="f3e97-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="f3e97-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="f3e97-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f3e97-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f3e97-113">Özel durum oluşturdu çerçevenin yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f3e97-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="f3e97-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f3e97-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f3e97-115">Oluşturulan özel durumun noktaya en yakın kullanıcı kodu çerçevenin yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f3e97-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="f3e97-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="f3e97-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f3e97-117">Catch işleyicisi içeren çerçevenin yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f3e97-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="f3e97-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="f3e97-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f3e97-119">`pStackPointer` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="f3e97-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f3e97-120">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e97-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="f3e97-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3e97-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e97-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3e97-122">Requirements</span></span>  
 <span data-ttu-id="f3e97-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e97-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e97-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3e97-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3e97-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3e97-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3e97-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e97-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e97-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3e97-127">See also</span></span>
- [<span data-ttu-id="f3e97-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3e97-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="f3e97-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f3e97-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
