---
title: Icordebugcode arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db2fe1e854069d9b5d566fc00420615e0c06b3d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575953"
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="13e91-102">Icordebugcode arabirimi1</span><span class="sxs-lookup"><span data-stu-id="13e91-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="13e91-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="13e91-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13e91-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="13e91-104">Methods</span></span>  
  
|<span data-ttu-id="13e91-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="13e91-105">Method</span></span>|<span data-ttu-id="13e91-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13e91-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13e91-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="13e91-108">Belirtilen uzaklıkta bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13e91-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="13e91-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="13e91-110">Kod kesiminin göreli sanal adres (RVA) alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="13e91-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="13e91-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="13e91-112">Ayrıştırma için biçimlendirilmiş belirtilen işlevi tüm kod alır.</span><span class="sxs-lookup"><span data-stu-id="13e91-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="13e91-113">Bu yöntem kullanım dışı; kullanma [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="13e91-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="13e91-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="13e91-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="13e91-115">Not implemented.</span></span>|  
|[<span data-ttu-id="13e91-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="13e91-117">"Bu ile ilişkili ICorDebugFunction" alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="13e91-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="13e91-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="13e91-119">Eşlemeleri için yerel uzaklıklar MSIL uzaklıkları temsil eden "Cor_debug_ıl_to_natıve_map" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="13e91-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="13e91-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="13e91-121">Bu tarafından temsil edilen ikili kod bayt cinsinden boyutunu alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="13e91-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="13e91-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="13e91-123">Kod sürümünü tanımlayan bir tabanlı sayısını alır, bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="13e91-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="13e91-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13e91-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="13e91-125">Belirten bir değer alır olup bu `ICorDebugCode` MSIL derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="13e91-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13e91-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13e91-126">Remarks</span></span>  
 <span data-ttu-id="13e91-127">`ICorDebugCode` MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="13e91-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="13e91-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesne sıfır veya bir olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="13e91-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="13e91-129">Yerel kod temsil eden bir "ICorDebugFunction" nesne herhangi bir sayıda olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="13e91-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13e91-130">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="13e91-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e91-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13e91-131">Requirements</span></span>  
 <span data-ttu-id="13e91-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e91-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e91-133">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13e91-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13e91-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13e91-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13e91-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e91-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e91-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13e91-136">See also</span></span>

- [<span data-ttu-id="13e91-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13e91-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="13e91-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="13e91-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
