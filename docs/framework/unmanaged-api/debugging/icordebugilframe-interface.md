---
description: ': ICorDebugILFrame Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 251fa18151ff286bee3e1bcf7707bf5f7145b4f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791367"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="b5e33-103">ICorDebugILFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5e33-103">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="b5e33-104">Microsoft ara dili (MSIL) kodunun yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b5e33-104">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="b5e33-105">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-105">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5e33-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b5e33-106">Methods</span></span>  
  
|<span data-ttu-id="b5e33-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5e33-107">Method</span></span>|<span data-ttu-id="b5e33-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5e33-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5e33-109">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-109">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="b5e33-110">Belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-110">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="b5e33-111">EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-111">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="b5e33-112">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-112">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="b5e33-113">EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-113">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="b5e33-114">Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-114">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="b5e33-115">GetArgument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-115">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="b5e33-116">Bu MSIL yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-116">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="b5e33-117">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-117">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="b5e33-118">Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-118">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="b5e33-119">GetLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-119">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="b5e33-120">Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-120">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="b5e33-121">GetStackDepth Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-121">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="b5e33-122">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="b5e33-122">Not implemented.</span></span>|  
|[<span data-ttu-id="b5e33-123">GetStackValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-123">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="b5e33-124">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="b5e33-124">Not implemented.</span></span>|  
|[<span data-ttu-id="b5e33-125">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e33-125">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="b5e33-126">Yönerge işaretçisini MSIL kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5e33-126">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5e33-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5e33-127">Remarks</span></span>  

 <span data-ttu-id="b5e33-128">`ICorDebugILFrame`Arabirim, özelleştirilmiş bir ICorDebugFrame arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="b5e33-128">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="b5e33-129">MSIL kod çerçeveleri ya da tam zamanında (JıT) derlenmiş çerçeveler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5e33-129">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="b5e33-130">JıT ile derlenen çerçeveler hem arabirimini hem de `ICorDebugILFrame` ICorDebugNativeFrame arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b5e33-130">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5e33-131">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b5e33-131">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5e33-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5e33-132">Requirements</span></span>  

 <span data-ttu-id="b5e33-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5e33-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e33-134">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b5e33-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5e33-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b5e33-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5e33-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5e33-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e33-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5e33-137">See also</span></span>

- [<span data-ttu-id="b5e33-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b5e33-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
