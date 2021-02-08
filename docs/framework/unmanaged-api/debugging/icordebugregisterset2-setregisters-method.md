---
description: 'Daha fazla bilgi edinin: ICorDebugRegisterSet2:: Setyazmaçları yöntemi'
title: ICorDebugRegisterSet2::SetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: d58717be34e146def2a54bb49d6cd58dde7564c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794760"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="57631-103">ICorDebugRegisterSet2::SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57631-103">ICorDebugRegisterSet2::SetRegisters Method</span></span>

<span data-ttu-id="57631-104">`SetRegisters` .NET Framework sürüm 2,0 ' de uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="57631-104">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="57631-105">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="57631-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57631-106">[ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md)gibi daha üst düzey işlemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="57631-106">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57631-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="57631-107">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="57631-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57631-108">Requirements</span></span>  

 <span data-ttu-id="57631-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57631-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57631-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57631-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57631-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="57631-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57631-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57631-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57631-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57631-113">See also</span></span>

- [<span data-ttu-id="57631-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57631-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="57631-115">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57631-115">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
