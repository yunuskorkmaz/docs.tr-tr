---
title: Icordebugcode Interface1
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
ms.openlocfilehash: 37917577c802514fcebc3ea0792cbce9bb8a7345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414085"
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="0babf-102">Icordebugcode Interface1</span><span class="sxs-lookup"><span data-stu-id="0babf-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="0babf-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0babf-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0babf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0babf-104">Methods</span></span>  
  
|<span data-ttu-id="0babf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0babf-105">Method</span></span>|<span data-ttu-id="0babf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0babf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0babf-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="0babf-108">Belirtilen uzaklıkta bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0babf-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="0babf-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="0babf-110">Kod kesimi göreli sanal adres (RAV) alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0babf-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="0babf-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="0babf-112">Belirtilen işlev için ayrıştırılmış biçimlendirilmiş tüm kodu alır.</span><span class="sxs-lookup"><span data-stu-id="0babf-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="0babf-113">Bu yöntem kullanım dışı bırakıldı; kullanmak [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="0babf-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="0babf-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="0babf-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="0babf-115">Not implemented.</span></span>|  
|[<span data-ttu-id="0babf-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="0babf-117">"Bu ile ilişkili ICorDebugFunction" alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="0babf-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="0babf-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="0babf-119">Eşlemeleri MSIL uzaklıkları yerel uzaklıkları temsil "Cor_debug_ıl_to_natıve_map" örnekleri dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="0babf-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="0babf-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="0babf-121">Bu tarafından temsil edilen ikili kod bayt cinsinden boyutu alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="0babf-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="0babf-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="0babf-123">Kod sürümünü belirleyen tabanlı numarasını alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0babf-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="0babf-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0babf-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="0babf-125">Gösteren bir değer alır olup olmadığını bu `ICorDebugCode` MSIL içinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="0babf-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0babf-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0babf-126">Remarks</span></span>  
 <span data-ttu-id="0babf-127">`ICorDebugCode` MSIL veya yerel koda temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="0babf-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="0babf-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesne sıfır veya bir olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0babf-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="0babf-129">Yerel kod temsil eden bir "ICorDebugFunction" nesne herhangi bir sayıda olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0babf-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0babf-130">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0babf-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0babf-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0babf-131">Requirements</span></span>  
 <span data-ttu-id="0babf-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0babf-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0babf-133">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0babf-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0babf-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0babf-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0babf-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0babf-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0babf-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0babf-136">See Also</span></span>  
    
 [<span data-ttu-id="0babf-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0babf-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="0babf-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0babf-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
