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
ms.openlocfilehash: eba86c09197aad6bac284c52fe164432e197c6f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378256"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="2347f-102">ICorDebugRegisterSet::SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2347f-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="2347f-103">`SetRegisters`.NET Framework sürüm 2,0 ' de uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="2347f-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2347f-104">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="2347f-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2347f-105">[ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md)gibi daha üst düzey işlemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2347f-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2347f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2347f-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2347f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2347f-107">Requirements</span></span>  
 <span data-ttu-id="2347f-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2347f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2347f-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2347f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2347f-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2347f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2347f-111">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="2347f-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2347f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2347f-112">See also</span></span>

- [<span data-ttu-id="2347f-113">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2347f-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="2347f-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2347f-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
