---
description: ': ICorDebugCode arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ce67c48501783bbe00152f0ba2c224e6e7dde6d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711160"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="2f5ea-103">ICorDebugCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-103">ICorDebugCode Interface</span></span>

<span data-ttu-id="2f5ea-104">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-104">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f5ea-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f5ea-105">Methods</span></span>  
  
|<span data-ttu-id="2f5ea-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2f5ea-106">Method</span></span>|<span data-ttu-id="2f5ea-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f5ea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f5ea-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-108">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="2f5ea-109">Belirtilen uzaklığa bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-109">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="2f5ea-110">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-110">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="2f5ea-111">Bu temsil eden kod kesiminin göreli sanal adresini (RVA) alır `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="2f5ea-111">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="2f5ea-112">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-112">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="2f5ea-113">Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-113">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="2f5ea-114">Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-114">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="2f5ea-115">GetEnCRemapSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-115">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="2f5ea-116">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-116">Not implemented.</span></span>|  
|[<span data-ttu-id="2f5ea-117">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-117">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="2f5ea-118">Bu ile ilişkili "ICorDebugFunction" öğesini alır `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="2f5ea-118">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="2f5ea-119">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-119">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="2f5ea-120">MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-120">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="2f5ea-121">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-121">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="2f5ea-122">Bu tarafından temsil edilen ikili kodun boyutunu bayt cinsinden alır `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="2f5ea-122">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="2f5ea-123">GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="2f5ea-123">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="2f5ea-124">Bu temsil eden kodun sürümünü tanımlayan tek tabanlı sayıyı alır `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="2f5ea-124">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="2f5ea-125">IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-125">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="2f5ea-126">Bu değerin `ICorDebugCode` MSIL 'de derlenip derlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-126">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f5ea-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f5ea-127">Remarks</span></span>  

 <span data-ttu-id="2f5ea-128">`ICorDebugCode` MSIL veya yerel kod temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-128">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="2f5ea-129">MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesinin, kendisiyle ilişkilendirilmiş sıfır veya bir `ICorDebugCode` nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-129">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="2f5ea-130">Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesne içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-130">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f5ea-131">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-131">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f5ea-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f5ea-132">Requirements</span></span>  

 <span data-ttu-id="2f5ea-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5ea-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5ea-134">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f5ea-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f5ea-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f5ea-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f5ea-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5ea-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5ea-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f5ea-137">See also</span></span>

- [<span data-ttu-id="2f5ea-138">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f5ea-138">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="2f5ea-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2f5ea-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
