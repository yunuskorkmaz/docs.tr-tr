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
ms.openlocfilehash: c01346b42fff812f8358482ae0e8570c03ee9231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912808"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="6be58-102">ICorDebugNativeFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6be58-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="6be58-103">Yerel çerçeveler için kullanılan ICorDebugFrame 'in özelleştirilmiş bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="6be58-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6be58-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6be58-104">Methods</span></span>  
  
|<span data-ttu-id="6be58-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6be58-105">Method</span></span>|<span data-ttu-id="6be58-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be58-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6be58-107">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="6be58-108">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="6be58-109">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="6be58-110">Yığın çerçevesinin sapmasını yerel koda alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="6be58-111">GetLocalDoubleRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="6be58-112">Bir bağımsız değişkenin veya yerel bir karenin iki bellek kaydı içinde depolanan yerel değişkenin değerini temsil eden bir ICorDebugValue için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="6be58-113">GetLocalMemoryRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="6be58-114">, Düşük bitlerin belirtilen kasada `ICorDebugValue` depolandığı ve yüksek bitlerin belirtilen bellek adresinde depolandığı yerel bir değişkenin değerini temsil eden bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="6be58-115">GetLocalMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="6be58-116">Belirtilen bellek adresinde depolanan yerel `ICorDebugValue` bir değişkenin değerini temsil eden bir işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="6be58-117">GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="6be58-118">Bir `ICorDebugValue` yerel değişkenin değerini temsil eden bir işaretçi alır, bu, yüksek bitlerin belirtilen kasada depolandığı ve düşük bitlerin belirtilen bellek adresinde depolandığı bir.</span><span class="sxs-lookup"><span data-stu-id="6be58-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="6be58-119">GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="6be58-120">Bir bağımsız değişkenin veya belirtilen `ICorDebugValue` yerel kasada depolanan yerel değişkenin değerini temsil eden bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="6be58-121">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="6be58-122">Bu`ICorDebugNativeFrame`için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6be58-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="6be58-123">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6be58-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="6be58-124">Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6be58-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6be58-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6be58-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6be58-126">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6be58-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6be58-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6be58-127">Requirements</span></span>  
 <span data-ttu-id="6be58-128">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6be58-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6be58-129">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6be58-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6be58-130">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6be58-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6be58-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6be58-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be58-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6be58-132">See also</span></span>

- [<span data-ttu-id="6be58-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6be58-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
