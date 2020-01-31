---
title: 'Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 657649b97262a12639117defe7a9c546f08cfef5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782849"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="29439-102">Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="29439-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="29439-103">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="29439-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29439-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29439-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29439-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29439-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="29439-106">dışı Bu özel durum ayıklama olayı için yığın işaretçisinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="29439-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="29439-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29439-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29439-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29439-108">Remarks</span></span>  
 <span data-ttu-id="29439-109">Bu yığın işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="29439-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="29439-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="29439-110">Event type</span></span>|<span data-ttu-id="29439-111">`pStackPointer` değerinin anlamı</span><span class="sxs-lookup"><span data-stu-id="29439-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="29439-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="29439-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="29439-113">Özel durumu oluşturan çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="29439-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="29439-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="29439-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="29439-115">Kullanıcı kodu çerçevesinin yığın işaretçisi, oluşturulan özel durumun noktasına en yakın.</span><span class="sxs-lookup"><span data-stu-id="29439-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="29439-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="29439-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="29439-117">Catch işleyicisini içeren çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="29439-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="29439-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="29439-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="29439-119">`pStackPointer` **null**.</span><span class="sxs-lookup"><span data-stu-id="29439-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="29439-120">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29439-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="29439-121">Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29439-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29439-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29439-122">Requirements</span></span>  
 <span data-ttu-id="29439-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29439-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29439-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29439-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29439-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="29439-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29439-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29439-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29439-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29439-127">See also</span></span>

- [<span data-ttu-id="29439-128">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29439-128">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="29439-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29439-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
