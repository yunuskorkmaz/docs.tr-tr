---
title: ICorDebugNativeFrame Arabirimi
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
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994623"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="1a785-102">ICorDebugNativeFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a785-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="1a785-103">Yerel çerçevelere ilişkin kullanılan Icordebugframe öğesinin özelleşmiş uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1a785-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a785-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a785-104">Methods</span></span>  
  
|<span data-ttu-id="1a785-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1a785-105">Method</span></span>|<span data-ttu-id="1a785-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a785-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a785-107">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="1a785-108">Yerel kodda belirtilen uzaklık konuma yönerge işaretçisi ayarlama güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1a785-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="1a785-109">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="1a785-110">Yığın çerçeve uzaklığı yerel kod içine alır.</span><span class="sxs-lookup"><span data-stu-id="1a785-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="1a785-111">GetLocalDoubleRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="1a785-112">Bir bağımsız değişken veya yerel değişken bir yerel çerçeve iki bellek yazmaçlarda depolanan değerini temsil eden bir Icordebugvalue için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="1a785-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="1a785-113">GetLocalMemoryRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="1a785-114">Bir işaretçi alır bir `ICorDebugValue` biri düşük BITS belirtilen kayıt defterinde depolanır ve yüksek bit belirtilen bellek adresinde depolanan bir yerel değişkenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a785-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1a785-115">GetLocalMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="1a785-116">Bir işaretçi alır bir `ICorDebugValue` belirtilen bellek adresinde depolanan bir yerel değişkenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a785-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1a785-117">GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="1a785-118">Bir işaretçi alır bir `ICorDebugValue` biri yüksek bit belirtilen kayıt defterinde depolanır ve düşük BITS belirtilen bellek adresinde depolanan bir yerel değişkenin değerini temsil eder</span><span class="sxs-lookup"><span data-stu-id="1a785-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="1a785-119">GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="1a785-120">Bir işaretçi alır bir `ICorDebugValue` bağımsız değişken ya da belirtilen yerel kayıt defterinde depolanan bir yerel değişken değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a785-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="1a785-121">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="1a785-122">Bir işaretçi alır bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) için bunu kayıt temsil eden `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="1a785-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="1a785-123">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a785-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="1a785-124">Yönerge işaretçisi yerel kodda uzaklık belirtilen konuma ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1a785-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a785-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a785-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a785-126">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1a785-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a785-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a785-127">Requirements</span></span>  
 <span data-ttu-id="1a785-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a785-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a785-129">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a785-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a785-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a785-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a785-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a785-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a785-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a785-132">See also</span></span>

- [<span data-ttu-id="1a785-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a785-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
