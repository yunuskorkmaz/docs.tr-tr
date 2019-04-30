---
title: ICorDebugCode Arabirimi
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
ms.openlocfilehash: 9ca47eb5508907297a78dba1ab2b0a6d2b8ece0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750260"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="9f87a-102">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f87a-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="9f87a-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f87a-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f87a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9f87a-104">Methods</span></span>  
  
|<span data-ttu-id="9f87a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9f87a-105">Method</span></span>|<span data-ttu-id="9f87a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f87a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f87a-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="9f87a-108">Belirtilen uzaklıkta bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f87a-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="9f87a-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="9f87a-110">Kod kesiminin göreli sanal adres (RVA) alır bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f87a-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="9f87a-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="9f87a-112">Ayrıştırma için biçimlendirilmiş belirtilen işlevi tüm kod alır.</span><span class="sxs-lookup"><span data-stu-id="9f87a-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="9f87a-113">Bu yöntem kullanım dışı; kullanma [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="9f87a-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="9f87a-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="9f87a-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="9f87a-115">Not implemented.</span></span>|  
|[<span data-ttu-id="9f87a-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="9f87a-117">"Bu ile ilişkili ICorDebugFunction" alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="9f87a-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="9f87a-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="9f87a-119">Eşlemeleri için yerel uzaklıklar MSIL uzaklıkları temsil eden "Cor_debug_ıl_to_natıve_map" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="9f87a-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="9f87a-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="9f87a-121">Bu tarafından temsil edilen ikili kod bayt cinsinden boyutunu alır `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="9f87a-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="9f87a-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="9f87a-123">Kod sürümünü tanımlayan bir tabanlı sayısını alır, bu `ICorDebugCode` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f87a-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="9f87a-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f87a-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="9f87a-125">Belirten bir değer alır olup bu `ICorDebugCode` MSIL derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="9f87a-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f87a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f87a-126">Remarks</span></span>  
 <span data-ttu-id="9f87a-127">`ICorDebugCode` MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="9f87a-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="9f87a-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesne sıfır veya bir olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9f87a-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="9f87a-129">Yerel kod temsil eden bir "ICorDebugFunction" nesne herhangi bir sayıda olabilir `ICorDebugCode` ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9f87a-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f87a-130">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9f87a-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f87a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f87a-131">Requirements</span></span>  
 <span data-ttu-id="9f87a-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f87a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f87a-133">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f87a-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f87a-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f87a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f87a-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f87a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f87a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f87a-136">See also</span></span>

- [<span data-ttu-id="9f87a-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f87a-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="9f87a-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9f87a-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
