---
description: ': Icordebugexceptiondebugger gevent:: GetStackPointer metodu hakkında daha fazla bilgi edinin'
title: 'Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 5a62a5eb54fff1e94beebc222e3f18cc4655040f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693453"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="ff614-103">Icordebugexceptiondebugger gevent:: GetStackPointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff614-103">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>

<span data-ttu-id="ff614-104">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="ff614-104">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff614-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff614-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff614-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff614-106">Parameters</span></span>  

 `pStackPointer`  
 <span data-ttu-id="ff614-107">dışı Bu özel durum ayıklama olayı için yığın işaretçisinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff614-107">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="ff614-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ff614-108">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff614-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff614-109">Remarks</span></span>  

 <span data-ttu-id="ff614-110">Bu yığın işaretçisinin anlamı, aşağıdaki tabloda gösterildiği gibi, olay türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ff614-110">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff614-111">Olay türü</span><span class="sxs-lookup"><span data-stu-id="ff614-111">Event type</span></span>|<span data-ttu-id="ff614-112">Değerin anlamı `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="ff614-112">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="ff614-113">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ff614-113">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff614-114">Özel durumu oluşturan çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ff614-114">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="ff614-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ff614-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff614-116">Kullanıcı kodu çerçevesinin yığın işaretçisi, oluşturulan özel durumun noktasına en yakın.</span><span class="sxs-lookup"><span data-stu-id="ff614-116">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="ff614-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="ff614-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff614-118">Catch işleyicisini içeren çerçeve için yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ff614-118">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="ff614-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="ff614-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff614-120">`pStackPointer`**null**.</span><span class="sxs-lookup"><span data-stu-id="ff614-120">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ff614-121">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff614-121">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="ff614-122">Olay türü [ıcordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yönteminden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff614-122">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff614-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff614-123">Requirements</span></span>  

 <span data-ttu-id="ff614-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff614-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff614-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff614-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff614-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ff614-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff614-127">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff614-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff614-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff614-128">See also</span></span>

- [<span data-ttu-id="ff614-129">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff614-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="ff614-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff614-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
