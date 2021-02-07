---
description: ': ICorDebugNativeFrame arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e417184c9f1ca5136e1b4dba07820fd8242ae932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729140"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="efc93-103">ICorDebugNativeFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efc93-103">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="efc93-104">Yerel çerçeveler için kullanılan ICorDebugFrame 'in özelleştirilmiş bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="efc93-104">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efc93-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="efc93-105">Methods</span></span>  
  
|<span data-ttu-id="efc93-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="efc93-106">Method</span></span>|<span data-ttu-id="efc93-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efc93-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efc93-108">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-108">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="efc93-109">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="efc93-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="efc93-110">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-110">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="efc93-111">Yığın çerçevesinin sapmasını yerel koda alır.</span><span class="sxs-lookup"><span data-stu-id="efc93-111">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="efc93-112">GetLocalDoubleRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-112">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="efc93-113">Bir bağımsız değişkenin veya yerel bir karenin iki bellek kaydı içinde depolanan yerel değişkenin değerini temsil eden bir ICorDebugValue için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="efc93-113">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="efc93-114">GetLocalMemoryRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-114">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="efc93-115">`ICorDebugValue`, Düşük bitlerin belirtilen kasada depolandığı ve yüksek bitlerin belirtilen bellek adresinde depolandığı yerel bir değişkenin değerini temsil eden bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="efc93-115">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="efc93-116">GetLocalMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-116">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="efc93-117">`ICorDebugValue`Belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eden bir işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="efc93-117">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="efc93-118">GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-118">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="efc93-119">Bir `ICorDebugValue` yerel değişkenin değerini temsil eden bir işaretçi alır, bu, yüksek bitlerin belirtilen kasada depolandığı ve düşük bitlerin belirtilen bellek adresinde depolandığı bir.</span><span class="sxs-lookup"><span data-stu-id="efc93-119">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="efc93-120">GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-120">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="efc93-121">Bir `ICorDebugValue` bağımsız değişkenin veya belirtilen yerel kasada depolanan yerel değişkenin değerini temsil eden bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="efc93-121">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="efc93-122">GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="efc93-122">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="efc93-123">Bu için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) için bir işaretçi alır `ICorDebugNativeFrame` .</span><span class="sxs-lookup"><span data-stu-id="efc93-123">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="efc93-124">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc93-124">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="efc93-125">Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="efc93-125">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efc93-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efc93-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efc93-127">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="efc93-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc93-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efc93-128">Requirements</span></span>  

 <span data-ttu-id="efc93-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc93-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc93-130">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="efc93-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efc93-131">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="efc93-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efc93-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc93-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc93-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efc93-133">See also</span></span>

- [<span data-ttu-id="efc93-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="efc93-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
