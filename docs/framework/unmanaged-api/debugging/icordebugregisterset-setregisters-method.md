---
title: ICorDebugRegisterSet::SetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 4be5d2d9d891010e68cd6eb96cd4456e04d8c8b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712293"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="3f9fe-102">ICorDebugRegisterSet::SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f9fe-102">ICorDebugRegisterSet::SetRegisters Method</span></span>

<span data-ttu-id="3f9fe-103">`SetRegisters` .NET Framework sürüm 2,0 ' de uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="3f9fe-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3f9fe-104">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="3f9fe-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f9fe-105">[ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md)gibi daha üst düzey işlemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f9fe-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9fe-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f9fe-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3f9fe-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f9fe-107">Requirements</span></span>  

 <span data-ttu-id="3f9fe-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f9fe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f9fe-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f9fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f9fe-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f9fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f9fe-111">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3f9fe-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9fe-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f9fe-112">See also</span></span>

- [<span data-ttu-id="3f9fe-113">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f9fe-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="3f9fe-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f9fe-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
