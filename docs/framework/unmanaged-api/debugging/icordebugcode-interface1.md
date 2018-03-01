---
title: Icordebugcode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86659b624ef01922b6c5d1db9b3ae3697d0128b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="608a8-102">Icordebugcode Interface1</span><span class="sxs-lookup"><span data-stu-id="608a8-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="608a8-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="608a8-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="608a8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="608a8-104">Methods</span></span>  
  
|<span data-ttu-id="608a8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="608a8-105">Method</span></span>|<span data-ttu-id="608a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="608a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="608a8-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="608a8-108">Belirtilen uzaklıkta bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="608a8-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="608a8-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="608a8-110">Kod kesimi göreli sanal adres (RAV) alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="608a8-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="608a8-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="608a8-112">Belirtilen işlev için ayrıştırılmış biçimlendirilmiş tüm kodu alır.</span><span class="sxs-lookup"><span data-stu-id="608a8-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="608a8-113">Bu yöntem kullanım dışı bırakıldı; kullanmak [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="608a8-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="608a8-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="608a8-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="608a8-115">Not implemented.</span></span>|  
|[<span data-ttu-id="608a8-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="608a8-117">"Bu ile ilişkili ICorDebugFunction" alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="608a8-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="608a8-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="608a8-119">Eşlemeleri MSIL uzaklıkları yerel uzaklıkları temsil "Cor_debug_ıl_to_natıve_map" örnekleri dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="608a8-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="608a8-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="608a8-121">Bu tarafından temsil edilen ikili kod bayt cinsinden boyutu alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="608a8-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="608a8-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="608a8-123">Kod sürümünü belirleyen tabanlı numarasını alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="608a8-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="608a8-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="608a8-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="608a8-125">Gösteren bir değer alır olup olmadığını bu `ICorDebugCode` MSIL içinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="608a8-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="608a8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="608a8-126">Remarks</span></span>  
 <span data-ttu-id="608a8-127">`ICorDebugCode`MSIL veya yerel koda temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="608a8-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="608a8-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesne sıfır veya bir olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="608a8-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="608a8-129">Yerel kod temsil eden bir "ICorDebugFunction" nesne herhangi bir sayıda olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="608a8-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="608a8-130">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="608a8-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="608a8-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="608a8-131">Requirements</span></span>  
 <span data-ttu-id="608a8-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="608a8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="608a8-133">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="608a8-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="608a8-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="608a8-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="608a8-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="608a8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608a8-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="608a8-136">See Also</span></span>  
    
 [<span data-ttu-id="608a8-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="608a8-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="608a8-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="608a8-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
