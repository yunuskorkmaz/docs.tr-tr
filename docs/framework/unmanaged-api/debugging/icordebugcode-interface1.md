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
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960788"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="d751d-102">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d751d-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="d751d-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d751d-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d751d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d751d-104">Methods</span></span>  
  
|<span data-ttu-id="d751d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d751d-105">Method</span></span>|<span data-ttu-id="d751d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d751d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d751d-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="d751d-108">Belirtilen uzaklığa bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d751d-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="d751d-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="d751d-110">Bu `ICorDebugCode` temsil eden kod kesiminin göreli sanal adresini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="d751d-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="d751d-112">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="d751d-113">Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d751d-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="d751d-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="d751d-115">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="d751d-115">Not implemented.</span></span>|  
|[<span data-ttu-id="d751d-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="d751d-117">Bu `ICorDebugCode`Ile Ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="d751d-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="d751d-119">MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="d751d-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="d751d-121">Bu `ICorDebugCode`tarafından temsil edilen ikili kodun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="d751d-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="d751d-123">Bu `ICorDebugCode` temsil eden kodun sürümünü tanımlayan tek tabanlı sayıyı alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="d751d-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d751d-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="d751d-125">Bu `ICorDebugCode` değerin MSIL 'de derlenip derlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d751d-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d751d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d751d-126">Remarks</span></span>  
 <span data-ttu-id="d751d-127">`ICorDebugCode`MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="d751d-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="d751d-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesinin, kendisiyle ilişkilendirilmiş sıfır veya bir `ICorDebugCode` nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d751d-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="d751d-129">Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesne içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d751d-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d751d-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d751d-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d751d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d751d-131">Requirements</span></span>  
 <span data-ttu-id="d751d-132">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d751d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d751d-133">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d751d-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d751d-134">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d751d-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d751d-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d751d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d751d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d751d-136">See also</span></span>

- [<span data-ttu-id="d751d-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d751d-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="d751d-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d751d-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
