---
title: Icordebugcode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode
helpviewer_keywords: ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7813381c345db3d14318dddd93df1b491b46549e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="7b50b-102">Icordebugcode Interface1</span><span class="sxs-lookup"><span data-stu-id="7b50b-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="7b50b-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b50b-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b50b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7b50b-104">Methods</span></span>  
  
|<span data-ttu-id="7b50b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7b50b-105">Method</span></span>|<span data-ttu-id="7b50b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b50b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b50b-107">CreateBreakpoint yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="7b50b-108">Belirtilen uzaklıkta bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b50b-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="7b50b-109">GetAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="7b50b-110">Kod kesimi göreli sanal adres (RAV) alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b50b-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="7b50b-111">GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="7b50b-112">Belirtilen işlev için ayrıştırılmış biçimlendirilmiş tüm kodu alır.</span><span class="sxs-lookup"><span data-stu-id="7b50b-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="7b50b-113">Bu yöntem kullanım dışı bırakıldı; kullanmak [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="7b50b-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="7b50b-114">GetEnCRemapSequencePoints yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="7b50b-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="7b50b-115">Not implemented.</span></span>|  
|[<span data-ttu-id="7b50b-116">GetFunction yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="7b50b-117">"Bu ile ilişkili ICorDebugFunction" alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7b50b-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="7b50b-118">Getıltonativemapping yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="7b50b-119">Eşlemeleri MSIL uzaklıkları yerel uzaklıkları temsil "Cor_debug_ıl_to_natıve_map" örnekleri dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="7b50b-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="7b50b-120">GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="7b50b-121">Bu tarafından temsil edilen ikili kod bayt cinsinden boyutu alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7b50b-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="7b50b-122">GetVersionNumber yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="7b50b-123">Kod sürümünü belirleyen tabanlı numarasını alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b50b-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="7b50b-124">Isıl yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b50b-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="7b50b-125">Gösteren bir değer alır olup olmadığını bu `ICorDebugCode` MSIL içinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="7b50b-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b50b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b50b-126">Remarks</span></span>  
 <span data-ttu-id="7b50b-127">`ICorDebugCode`MSIL veya yerel koda temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="7b50b-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="7b50b-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesne sıfır veya bir olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7b50b-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="7b50b-129">Yerel kod temsil eden bir "ICorDebugFunction" nesne herhangi bir sayıda olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7b50b-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b50b-130">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7b50b-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b50b-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b50b-131">Requirements</span></span>  
 <span data-ttu-id="7b50b-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b50b-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b50b-133">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b50b-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b50b-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b50b-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b50b-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b50b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b50b-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b50b-136">See Also</span></span>  
    
 [<span data-ttu-id="7b50b-137">Icordebugcode3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b50b-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="7b50b-138">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7b50b-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
