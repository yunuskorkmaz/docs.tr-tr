---
title: Icordebugnativeframe Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7996d5800e99d8e6161e24f34604aff3e4e906bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422009"
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="4f75c-102">Icordebugnativeframe Interface1</span><span class="sxs-lookup"><span data-stu-id="4f75c-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="4f75c-103">Yerel çerçeveler için kullanılan Icordebugframe, özelleştirilmiş bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="4f75c-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f75c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4f75c-104">Methods</span></span>  
  
|<span data-ttu-id="4f75c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4f75c-105">Method</span></span>|<span data-ttu-id="4f75c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f75c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f75c-107">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="4f75c-108">Yönerge işaretçisi belirtilen uzaklık konuma yerel kodda ayarlamak güvenli olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4f75c-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="4f75c-109">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="4f75c-110">Yığın çerçeve uzaklığı yerel kod içine alır.</span><span class="sxs-lookup"><span data-stu-id="4f75c-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="4f75c-111">GetLocalDoubleRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="4f75c-112">Bir işaretçi bir bağımsız değişken veya yerel bir çerçeve iki bellek kayıtlarında depolanan yerel değişken değerini temsil eden bir Icordebugvalue alır.</span><span class="sxs-lookup"><span data-stu-id="4f75c-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="4f75c-113">GetLocalMemoryRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="4f75c-114">Bir işaretçi alır bir `ICorDebugValue` biri düşük BITS belirtilen kayıt defterinde depolanır ve yüksek bit belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f75c-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="4f75c-115">GetLocalMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="4f75c-116">Bir işaretçi alır bir `ICorDebugValue` belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f75c-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="4f75c-117">GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="4f75c-118">Bir işaretçi alır bir `ICorDebugValue` biri yüksek bit belirtilen kayıt defterinde depolanır ve düşük BITS belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eder</span><span class="sxs-lookup"><span data-stu-id="4f75c-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="4f75c-119">GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="4f75c-120">Bir işaretçi alır bir `ICorDebugValue` bağımsız değişken veya belirtilen yerel kayıt defterinde depolanan yerel bir değişken değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f75c-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="4f75c-121">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="4f75c-122">Bir işaretçi alır bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) temsil eden bu ayarla kayıt `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="4f75c-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="4f75c-123">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f75c-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="4f75c-124">Yönerge işaretçisi yerel kodda belirtilen uzaklık konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f75c-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f75c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f75c-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f75c-126">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4f75c-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f75c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f75c-127">Requirements</span></span>  
 <span data-ttu-id="4f75c-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f75c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f75c-129">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f75c-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f75c-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f75c-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f75c-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f75c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f75c-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f75c-132">See Also</span></span>  
 [<span data-ttu-id="4f75c-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f75c-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
