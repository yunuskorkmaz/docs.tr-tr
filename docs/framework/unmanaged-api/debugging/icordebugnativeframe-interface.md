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
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792789"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="24878-102">ICorDebugNativeFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24878-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="24878-103">Yerel çerçeveler için kullanılan ICorDebugFrame 'in özelleştirilmiş bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="24878-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24878-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="24878-104">Methods</span></span>  
  
|<span data-ttu-id="24878-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="24878-105">Method</span></span>|<span data-ttu-id="24878-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24878-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24878-107">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="24878-108">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="24878-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="24878-109">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="24878-110">Yığın çerçevesinin sapmasını yerel koda alır.</span><span class="sxs-lookup"><span data-stu-id="24878-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="24878-111">GetLocalDoubleRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="24878-112">Bir bağımsız değişkenin veya yerel bir karenin iki bellek kaydı içinde depolanan yerel değişkenin değerini temsil eden bir ICorDebugValue için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="24878-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="24878-113">GetLocalMemoryRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="24878-114">, Düşük bitlerin belirtilen kasada depolandığı ve yüksek bitlerin belirtilen bellek adresinde depolandığı bir yerel değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="24878-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="24878-115">GetLocalMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="24878-116">Belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="24878-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="24878-117">GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="24878-118">Yüksek bitlerin belirtilen kasada depolandığı ve düşük bitlerin belirtilen bellek adresinde depolandığı bir yerel değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır</span><span class="sxs-lookup"><span data-stu-id="24878-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="24878-119">GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="24878-120">Bir bağımsız değişkenin veya belirtilen yerel kasada depolanan yerel değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="24878-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="24878-121">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="24878-122">Bu `ICorDebugNativeFrame`için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="24878-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="24878-123">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24878-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="24878-124">Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24878-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24878-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24878-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24878-126">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="24878-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24878-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24878-127">Requirements</span></span>  
 <span data-ttu-id="24878-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24878-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24878-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="24878-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24878-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="24878-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24878-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24878-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24878-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24878-132">See also</span></span>

- [<span data-ttu-id="24878-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="24878-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
