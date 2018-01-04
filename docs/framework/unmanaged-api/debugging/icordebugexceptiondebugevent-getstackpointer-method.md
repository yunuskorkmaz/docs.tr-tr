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
ms.workload: dotnet
ms.openlocfilehash: 1b9096bbb494036156a528d8f9e940630f555f6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="55cc9-102">ICorDebugExceptionDebugEvent::GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="55cc9-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="55cc9-103">Yığın işaretçisi için bu özel durum hata ayıklama olayı alır.</span><span class="sxs-lookup"><span data-stu-id="55cc9-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55cc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55cc9-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55cc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55cc9-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="55cc9-106">[out] Bu özel durumun yığın işaretçisi adresini gösteren bir işaretçi olay hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="55cc9-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="55cc9-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="55cc9-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55cc9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55cc9-108">Remarks</span></span>  
 <span data-ttu-id="55cc9-109">Bu yığın işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="55cc9-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="55cc9-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="55cc9-110">Event type</span></span>|<span data-ttu-id="55cc9-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="55cc9-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="55cc9-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="55cc9-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="55cc9-113">Özel durum oluşturdu çerçeve yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55cc9-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="55cc9-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="55cc9-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="55cc9-115">Oluşturulan özel durum noktasına yakın kullanıcı kodu çerçeve yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55cc9-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="55cc9-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="55cc9-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="55cc9-117">Catch işleyicisi içeren çerçeveyi yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55cc9-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="55cc9-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="55cc9-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="55cc9-119">`pStackPointer`olan **null**.</span><span class="sxs-lookup"><span data-stu-id="55cc9-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="55cc9-120">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55cc9-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="55cc9-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55cc9-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55cc9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55cc9-122">Requirements</span></span>  
 <span data-ttu-id="55cc9-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55cc9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55cc9-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55cc9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55cc9-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55cc9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55cc9-126">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55cc9-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cc9-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55cc9-127">See Also</span></span>  
 [<span data-ttu-id="55cc9-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55cc9-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="55cc9-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="55cc9-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
