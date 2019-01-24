---
title: Icordebugılframe arabirimi1
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
ms.openlocfilehash: 73cf7f26b228fa5aa458a6de312df3bf777e0206
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580518"
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="fedfd-102">Icordebugılframe arabirimi1</span><span class="sxs-lookup"><span data-stu-id="fedfd-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="fedfd-103">Microsoft Ara dili (MSIL) kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fedfd-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="fedfd-104">Icordebugframe arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="fedfd-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fedfd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fedfd-105">Methods</span></span>  
  
|<span data-ttu-id="fedfd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fedfd-106">Method</span></span>|<span data-ttu-id="fedfd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fedfd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fedfd-108">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="fedfd-109">Belirtilen uzaklık konuma yönerge işaretçisi ayarlama güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="fedfd-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="fedfd-110">EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="fedfd-111">Bir numaralandırıcı bu çerçeveye bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="fedfd-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="fedfd-112">EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="fedfd-113">Bir numaralandırıcı bu çerçevesinde yerel değişkenler için alır.</span><span class="sxs-lookup"><span data-stu-id="fedfd-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="fedfd-114">GetArgument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="fedfd-115">Bu MSIL yığın çerçevesi içinde belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="fedfd-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="fedfd-116">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="fedfd-117">Yönerge işaretçisi değerini ve nasıl yönerge işaretçisini değerini edinilen açıklayan bir karşılaştırmaya değerini alır.</span><span class="sxs-lookup"><span data-stu-id="fedfd-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="fedfd-118">GetLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="fedfd-119">Bu MSIL yığın çerçevesi içinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="fedfd-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="fedfd-120">GetStackDepth Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="fedfd-121">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="fedfd-121">Not implemented.</span></span>|  
|[<span data-ttu-id="fedfd-122">GetStackValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="fedfd-123">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="fedfd-123">Not implemented.</span></span>|  
|[<span data-ttu-id="fedfd-124">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedfd-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="fedfd-125">MSIL kodunu belirtilen uzaklık konuma yönerge işaretçisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fedfd-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fedfd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fedfd-126">Remarks</span></span>  
 <span data-ttu-id="fedfd-127">`ICorDebugILFrame` Özelleştirilmiş bir Icordebugframe arabirimi arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="fedfd-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="fedfd-128">Kullanıldığı çerçeveler için MSIL kod çerçeveleri veya just-in-time (JIT) için derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="fedfd-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="fedfd-129">JIT olarak derlenmiş çerçeveleri her ikisini de uygulamak `ICorDebugILFrame` arabirimi ve Icordebugnativeframe arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fedfd-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fedfd-130">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fedfd-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fedfd-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fedfd-131">Requirements</span></span>  
 <span data-ttu-id="fedfd-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fedfd-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fedfd-133">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fedfd-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fedfd-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fedfd-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fedfd-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fedfd-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedfd-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fedfd-136">See also</span></span>
- [<span data-ttu-id="fedfd-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fedfd-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
