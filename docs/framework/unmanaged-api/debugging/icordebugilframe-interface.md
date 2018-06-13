---
title: Icordebugılframe Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a97704e00278e19181df569f108f428cb1ec90f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417751"
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="bdf10-102">Icordebugılframe Interface1</span><span class="sxs-lookup"><span data-stu-id="bdf10-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="bdf10-103">Yığın çerçevesi Microsoft Ara dili (MSIL) kodunun temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bdf10-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="bdf10-104">Bu arabirim Icordebugframe arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdf10-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bdf10-105">Methods</span></span>  
  
|<span data-ttu-id="bdf10-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bdf10-106">Method</span></span>|<span data-ttu-id="bdf10-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdf10-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdf10-108">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="bdf10-109">Yönerge işaretçisi belirtilen uzaklık konuma ayarlamak güvenli olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="bdf10-110">EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="bdf10-111">Bir numaralandırıcı Bu çerçevede bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="bdf10-112">EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="bdf10-113">Bir numaralandırıcı yerel değişkenler için bu çerçevede alır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="bdf10-114">GetArgument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="bdf10-115">Belirtilen bağımsız değişkenin değeri bu MSIL yığın çerçevesinde alır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="bdf10-116">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="bdf10-117">Yönerge işaretçisi değerini ve nasıl yönerge işaretçisi değerini edinilen açıklayan Bitsel bir birleşimi değeri alır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="bdf10-118">GetLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="bdf10-119">Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="bdf10-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="bdf10-120">GetStackDepth Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="bdf10-121">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bdf10-121">Not implemented.</span></span>|  
|[<span data-ttu-id="bdf10-122">GetStackValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="bdf10-123">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bdf10-123">Not implemented.</span></span>|  
|[<span data-ttu-id="bdf10-124">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdf10-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="bdf10-125">Yönerge işaretçisi MSIL kodda belirtilen uzaklık konumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bdf10-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdf10-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdf10-126">Remarks</span></span>  
 <span data-ttu-id="bdf10-127">`ICorDebugILFrame` Özel Icordebugframe arabirimi bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="bdf10-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="bdf10-128">Kullanıldığı MSIL kod çerçeveleri için veya tam zamanında (JIT) için çerçeveler derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="bdf10-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="bdf10-129">JIT derlenmiş çerçeveleri her ikisini de uygulamak `ICorDebugILFrame` arabirimi ve Icordebugnativeframe arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bdf10-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdf10-130">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bdf10-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf10-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdf10-131">Requirements</span></span>  
 <span data-ttu-id="bdf10-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf10-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf10-133">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdf10-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdf10-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf10-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf10-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf10-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf10-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bdf10-136">See Also</span></span>  
 [<span data-ttu-id="bdf10-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bdf10-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
