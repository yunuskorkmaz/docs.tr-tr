---
title: ICorDebugExceptionDebugEvent::GetStackPointer yöntemi
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b30fae0e0a6b6cca64581ecafe78621c8f0068b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754301"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="52cb5-102">ICorDebugExceptionDebugEvent::GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cb5-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="52cb5-103">Bu özel durum hata ayıklama olayı için yığın işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="52cb5-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52cb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52cb5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52cb5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52cb5-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="52cb5-106">[out] Olay hata ayıklama bu özel durumun yığın işaretçisinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="52cb5-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="52cb5-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="52cb5-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52cb5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52cb5-108">Remarks</span></span>  
 <span data-ttu-id="52cb5-109">Bu yığın işaretçisi anlamını, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="52cb5-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="52cb5-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="52cb5-110">Event type</span></span>|<span data-ttu-id="52cb5-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="52cb5-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="52cb5-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="52cb5-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="52cb5-113">Özel durum oluşturdu çerçevenin yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52cb5-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="52cb5-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="52cb5-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="52cb5-115">Oluşturulan özel durumun noktaya en yakın kullanıcı kodu çerçevenin yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52cb5-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="52cb5-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="52cb5-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="52cb5-117">Catch işleyicisi içeren çerçevenin yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52cb5-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="52cb5-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="52cb5-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="52cb5-119">`pStackPointer` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="52cb5-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="52cb5-120">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52cb5-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="52cb5-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52cb5-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52cb5-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52cb5-122">Requirements</span></span>  
 <span data-ttu-id="52cb5-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52cb5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52cb5-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52cb5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52cb5-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52cb5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52cb5-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52cb5-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cb5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52cb5-127">See also</span></span>

- [<span data-ttu-id="52cb5-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52cb5-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="52cb5-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="52cb5-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
