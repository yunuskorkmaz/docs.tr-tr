---
title: ICorDebugExceptionDebugEvent::GetNativeIP yöntemi
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2455e52e46edd7fc8d4d6e8b003d3ebfd87ea07f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085839"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="ff7d7-102">ICorDebugExceptionDebugEvent::GetNativeIP yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff7d7-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="ff7d7-103">Bu özel durum hata ayıklama olayı için yerel yönerge işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff7d7-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff7d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff7d7-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="ff7d7-106">[out] Olay hata ayıklama bu özel durumun yönerge işaretçisini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="ff7d7-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff7d7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff7d7-108">Remarks</span></span>  
 <span data-ttu-id="ff7d7-109">Bu yönerge işaretçisini anlamını, aşağıdaki tabloda gösterildiği gibi olay türüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff7d7-110">Olay türü</span><span class="sxs-lookup"><span data-stu-id="ff7d7-110">Event type</span></span>|<span data-ttu-id="ff7d7-111">Anlamını `pStackPointer` değeri</span><span class="sxs-lookup"><span data-stu-id="ff7d7-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="ff7d7-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ff7d7-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff7d7-113">Hataya neden olan yönergeyi adresi.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="ff7d7-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ff7d7-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff7d7-115">Kod adresi çerçevede gösterilen [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi nerede sürdürebilir, hiçbir özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="ff7d7-116">Özel durum olabilir veya catch bloğu gibi farklı bir kod neden olmaz bir `try/catch/finally` bu çerçeveye yürütülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="ff7d7-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="ff7d7-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="ff7d7-118">Kodun nereye adres `catch` işleyici yürütme belirttiği çerçevesinde başlayacak [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="ff7d7-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="ff7d7-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pIP` <span data-ttu-id="ff7d7-120">0'dır.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-120">is 0.</span></span>|  
  
 <span data-ttu-id="ff7d7-121">Olay türü kullanılabilir [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff7d7-122">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff7d7-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff7d7-123">Requirements</span></span>  
 <span data-ttu-id="ff7d7-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff7d7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff7d7-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff7d7-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff7d7-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff7d7-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ff7d7-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ff7d7-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ff7d7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff7d7-128">See also</span></span>

- [<span data-ttu-id="ff7d7-129">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff7d7-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="ff7d7-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff7d7-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
