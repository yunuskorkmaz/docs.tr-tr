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
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893465"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="d2f3f-102">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="d2f3f-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2f3f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d2f3f-104">Methods</span></span>  
  
|<span data-ttu-id="d2f3f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2f3f-105">Method</span></span>|<span data-ttu-id="d2f3f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2f3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2f3f-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="d2f3f-108">Belirtilen uzaklığa bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="d2f3f-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="d2f3f-110">Bu `ICorDebugCode` temsil eden kod kesiminin göreli sanal ADRESINI (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="d2f3f-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="d2f3f-112">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="d2f3f-113">Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="d2f3f-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="d2f3f-115">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-115">Not implemented.</span></span>|  
|[<span data-ttu-id="d2f3f-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="d2f3f-117">Bu `ICorDebugCode`ile Ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="d2f3f-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="d2f3f-119">MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="d2f3f-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="d2f3f-121">Bu `ICorDebugCode`tarafından temsil edilen ikili kodun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="d2f3f-122">GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="d2f3f-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="d2f3f-123">Bu `ICorDebugCode` temsil eden kodun sürümünü tanımlayan tek tabanlı sayıyı alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="d2f3f-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="d2f3f-125">Bu `ICorDebugCode` değerin MSIL 'de derlenip derlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2f3f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2f3f-126">Remarks</span></span>  
 <span data-ttu-id="d2f3f-127">`ICorDebugCode`MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="d2f3f-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesinin, kendisiyle ilişkilendirilmiş sıfır veya bir `ICorDebugCode` nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="d2f3f-129">Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesne içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2f3f-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f3f-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2f3f-131">Requirements</span></span>  
 <span data-ttu-id="d2f3f-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f3f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f3f-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d2f3f-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2f3f-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d2f3f-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2f3f-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f3f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f3f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-136">See also</span></span>

- [<span data-ttu-id="d2f3f-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="d2f3f-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d2f3f-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
