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
ms.openlocfilehash: 8cb95fad4394e2ce9b7f922e720071d8c4434edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125586"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="2a41a-102">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a41a-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="2a41a-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a41a-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a41a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2a41a-104">Methods</span></span>  
  
|<span data-ttu-id="2a41a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a41a-105">Method</span></span>|<span data-ttu-id="2a41a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a41a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a41a-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="2a41a-108">Belirtilen uzaklığa bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a41a-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="2a41a-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="2a41a-110">Bu `ICorDebugCode` temsil ettiği kod segmentinin göreli sanal adresini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="2a41a-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="2a41a-112">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="2a41a-113">Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a41a-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="2a41a-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="2a41a-115">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="2a41a-115">Not implemented.</span></span>|  
|[<span data-ttu-id="2a41a-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="2a41a-117">Bu `ICorDebugCode`ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="2a41a-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="2a41a-119">MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="2a41a-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="2a41a-121">Bu `ICorDebugCode`temsil edilen ikili kodun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="2a41a-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="2a41a-123">Bu `ICorDebugCode` gösterdiği kodun sürümünü tanımlayan tek tabanlı sayıyı alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="2a41a-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a41a-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="2a41a-125">Bu `ICorDebugCode` MSIL 'de derlenmiş olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a41a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a41a-126">Remarks</span></span>  
 <span data-ttu-id="2a41a-127">`ICorDebugCode` MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="2a41a-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesi, kendisiyle ilişkilendirilmiş sıfır ya da bir `ICorDebugCode` nesnesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="2a41a-129">Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesnesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a41a-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2a41a-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a41a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a41a-131">Requirements</span></span>  
 <span data-ttu-id="2a41a-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a41a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a41a-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a41a-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a41a-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a41a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a41a-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a41a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a41a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a41a-136">See also</span></span>

- [<span data-ttu-id="2a41a-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a41a-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="2a41a-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2a41a-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
