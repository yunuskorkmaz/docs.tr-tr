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
ms.openlocfilehash: 4b24b3dfe6a931866acd7eba966811071ff39ea5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788935"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="df834-102">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df834-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="df834-103">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="df834-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df834-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="df834-104">Methods</span></span>  
  
|<span data-ttu-id="df834-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df834-105">Method</span></span>|<span data-ttu-id="df834-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df834-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df834-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="df834-108">Belirtilen uzaklığa bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df834-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="df834-109">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="df834-110">Bu `ICorDebugCode` temsil ettiği kod segmentinin göreli sanal adresini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="df834-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="df834-111">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="df834-112">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="df834-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="df834-113">Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="df834-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="df834-114">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="df834-115">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="df834-115">Not implemented.</span></span>|  
|[<span data-ttu-id="df834-116">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="df834-117">Bu `ICorDebugCode`ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="df834-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="df834-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="df834-119">MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="df834-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="df834-120">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="df834-121">Bu `ICorDebugCode`temsil edilen ikili kodun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="df834-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="df834-122">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="df834-123">Bu `ICorDebugCode` gösterdiği kodun sürümünü tanımlayan tek tabanlı sayıyı alır.</span><span class="sxs-lookup"><span data-stu-id="df834-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="df834-124">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df834-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="df834-125">Bu `ICorDebugCode` MSIL 'de derlenmiş olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="df834-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df834-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df834-126">Remarks</span></span>  
 <span data-ttu-id="df834-127">`ICorDebugCode` MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="df834-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="df834-128">MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesi, kendisiyle ilişkilendirilmiş sıfır ya da bir `ICorDebugCode` nesnesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="df834-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="df834-129">Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesnesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="df834-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df834-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="df834-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df834-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df834-131">Requirements</span></span>  
 <span data-ttu-id="df834-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df834-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df834-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df834-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df834-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df834-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df834-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df834-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df834-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df834-136">See also</span></span>

- [<span data-ttu-id="df834-137">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df834-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="df834-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df834-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
