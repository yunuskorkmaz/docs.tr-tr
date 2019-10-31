---
title: ICorDebugILFrame Arabirimi
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
ms.openlocfilehash: 01c247f838f66d1a77831755126a5a1f56870c1e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095141"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="1e149-102">ICorDebugILFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e149-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="1e149-103">Microsoft ara dili (MSIL) kodunun yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e149-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="1e149-104">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="1e149-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e149-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1e149-105">Methods</span></span>  
  
|<span data-ttu-id="1e149-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1e149-106">Method</span></span>|<span data-ttu-id="1e149-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e149-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e149-108">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="1e149-109">Belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1e149-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="1e149-110">EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="1e149-111">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1e149-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="1e149-112">EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="1e149-113">Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1e149-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="1e149-114">GetArgument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="1e149-115">Bu MSIL yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1e149-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="1e149-116">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="1e149-117">Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1e149-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="1e149-118">GetLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="1e149-119">Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1e149-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="1e149-120">GetStackDepth Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="1e149-121">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1e149-121">Not implemented.</span></span>|  
|[<span data-ttu-id="1e149-122">GetStackValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="1e149-123">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1e149-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1e149-124">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e149-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="1e149-125">Yönerge işaretçisini MSIL kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e149-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e149-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e149-126">Remarks</span></span>  
 <span data-ttu-id="1e149-127">`ICorDebugILFrame` arabirimi, özelleştirilmiş bir ICorDebugFrame arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="1e149-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="1e149-128">MSIL kod çerçeveleri ya da tam zamanında (JıT) derlenmiş çerçeveler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e149-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="1e149-129">JıT ile derlenen çerçeveler hem `ICorDebugILFrame` arabirimini hem de ICorDebugNativeFrame arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="1e149-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e149-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1e149-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e149-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e149-131">Requirements</span></span>  
 <span data-ttu-id="1e149-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e149-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e149-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1e149-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e149-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1e149-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e149-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e149-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e149-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e149-136">See also</span></span>

- [<span data-ttu-id="1e149-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1e149-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
