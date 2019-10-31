---
title: 'Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 688f5aec457298a43d95a35fdbc6e04e29a306a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084681"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="0cab7-102">Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cab7-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="0cab7-103">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="0cab7-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cab7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cab7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cab7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cab7-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="0cab7-106">dışı Bu özel durum ayıklama olayı için yığın işaretçisinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cab7-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="0cab7-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0cab7-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cab7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cab7-108">Remarks</span></span>  
 <span data-ttu-id="0cab7-109">Bu yığın işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cab7-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0cab7-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="0cab7-110">Event type</span></span>|<span data-ttu-id="0cab7-111">`pStackPointer` değerinin anlamı</span><span class="sxs-lookup"><span data-stu-id="0cab7-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="0cab7-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0cab7-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0cab7-113">Özel durumu oluşturan çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0cab7-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="0cab7-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0cab7-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0cab7-115">Kullanıcı kodu çerçevesinin yığın işaretçisi, oluşturulan özel durumun noktasına en yakın.</span><span class="sxs-lookup"><span data-stu-id="0cab7-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="0cab7-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="0cab7-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0cab7-117">Catch işleyicisini içeren çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0cab7-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="0cab7-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="0cab7-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0cab7-119">`pStackPointer` **null**.</span><span class="sxs-lookup"><span data-stu-id="0cab7-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0cab7-120">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cab7-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="0cab7-121">Olay türü [ıcordebugdebugger gevent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cab7-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cab7-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cab7-122">Requirements</span></span>  
 <span data-ttu-id="0cab7-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cab7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cab7-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0cab7-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cab7-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0cab7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cab7-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cab7-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cab7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cab7-127">See also</span></span>

- [<span data-ttu-id="0cab7-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cab7-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="0cab7-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0cab7-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
