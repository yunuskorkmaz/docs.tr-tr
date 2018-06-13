---
title: ICorDebugExceptionDebugEvent::GetStackPointer yöntemi
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e724b3a928a23bb44c3d1005024f803b5974e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415561"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="c734d-102">ICorDebugExceptionDebugEvent::GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="c734d-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="c734d-103">Yığın işaretçisi için bu özel durum hata ayıklama olayı alır.</span><span class="sxs-lookup"><span data-stu-id="c734d-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c734d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c734d-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c734d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c734d-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="c734d-106">[out] Bu özel durumun yığın işaretçisi adresini gösteren bir işaretçi olay hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="c734d-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="c734d-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c734d-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c734d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c734d-108">Remarks</span></span>  
 <span data-ttu-id="c734d-109">Bu yığın işaretçisi anlamı, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="c734d-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c734d-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="c734d-110">Event type</span></span>|<span data-ttu-id="c734d-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="c734d-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="c734d-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c734d-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c734d-113">Özel durum oluşturdu çerçeve yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c734d-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="c734d-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c734d-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c734d-115">Oluşturulan özel durum noktasına yakın kullanıcı kodu çerçeve yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c734d-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="c734d-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="c734d-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c734d-117">Catch işleyicisi içeren çerçeveyi yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c734d-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="c734d-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="c734d-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="c734d-119">`pStackPointer` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="c734d-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c734d-120">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c734d-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="c734d-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c734d-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c734d-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c734d-122">Requirements</span></span>  
 <span data-ttu-id="c734d-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c734d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c734d-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c734d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c734d-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c734d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c734d-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c734d-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c734d-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c734d-127">See Also</span></span>  
 [<span data-ttu-id="c734d-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c734d-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="c734d-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c734d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
