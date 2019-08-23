---
title: 'Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47f60b151166804d612292fb32b7ff154e417342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928199"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="e6fde-102">Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6fde-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="e6fde-103">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="e6fde-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6fde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6fde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6fde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6fde-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="e6fde-106">dışı Bu özel durum ayıklama olayı için yığın işaretçisinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6fde-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="e6fde-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e6fde-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6fde-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6fde-108">Remarks</span></span>  
 <span data-ttu-id="e6fde-109">Bu yığın işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6fde-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="e6fde-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="e6fde-110">Event type</span></span>|<span data-ttu-id="e6fde-111">`pStackPointer` Değerin anlamı</span><span class="sxs-lookup"><span data-stu-id="e6fde-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="e6fde-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="e6fde-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="e6fde-113">Özel durumu oluşturan çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6fde-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="e6fde-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="e6fde-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="e6fde-115">Kullanıcı kodu çerçevesinin yığın işaretçisi, oluşturulan özel durumun noktasına en yakın.</span><span class="sxs-lookup"><span data-stu-id="e6fde-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="e6fde-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="e6fde-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="e6fde-117">Catch işleyicisini içeren çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6fde-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="e6fde-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="e6fde-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="e6fde-119">`pStackPointer`**null**.</span><span class="sxs-lookup"><span data-stu-id="e6fde-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e6fde-120">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6fde-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="e6fde-121">Olay türü [ıcordebugdebugger gevent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6fde-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6fde-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6fde-122">Requirements</span></span>  
 <span data-ttu-id="e6fde-123">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6fde-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6fde-124">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6fde-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6fde-125">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6fde-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6fde-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6fde-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fde-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6fde-127">See also</span></span>

- [<span data-ttu-id="e6fde-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6fde-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="e6fde-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6fde-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
