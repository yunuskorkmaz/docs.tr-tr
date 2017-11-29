---
title: "ICorDebugExceptionDebugEvent::GetStackPointer yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17a7540c25eb1273add430c3a8ae01eea35497e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="8a1c7-102">ICorDebugExceptionDebugEvent::GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a1c7-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="8a1c7-103">Yığın işaretçisi için bu özel durum hata ayıklama olayı alır.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a1c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a1c7-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a1c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a1c7-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="8a1c7-106">[out] Bu özel durumun yığın işaretçisi adresini gösteren bir işaretçi olay hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="8a1c7-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a1c7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a1c7-108">Remarks</span></span>  
 <span data-ttu-id="8a1c7-109">Bu yığın işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="8a1c7-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="8a1c7-110">Event type</span></span>|<span data-ttu-id="8a1c7-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="8a1c7-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="8a1c7-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="8a1c7-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8a1c7-113">Özel durum oluşturdu çerçeve yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="8a1c7-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="8a1c7-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8a1c7-115">Oluşturulan özel durum noktasına yakın kullanıcı kodu çerçeve yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="8a1c7-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="8a1c7-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8a1c7-117">Catch işleyicisi içeren çerçeveyi yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="8a1c7-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="8a1c7-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="8a1c7-119">`pStackPointer`olan **null**.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8a1c7-120">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="8a1c7-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a1c7-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a1c7-122">Requirements</span></span>  
 <span data-ttu-id="8a1c7-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a1c7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a1c7-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a1c7-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a1c7-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a1c7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a1c7-126">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a1c7-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1c7-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a1c7-127">See Also</span></span>  
 [<span data-ttu-id="8a1c7-128">Icordebugexceptiondebugevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a1c7-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="8a1c7-129">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a1c7-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
