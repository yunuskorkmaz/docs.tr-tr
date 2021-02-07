---
description: ': ICorDebugRegisterSet:: Setyazmaçları yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7a83d9d01a392d7ed435292f45ee0c75765ced36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690684"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="e232f-103">ICorDebugRegisterSet::SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e232f-103">ICorDebugRegisterSet::SetRegisters Method</span></span>

<span data-ttu-id="e232f-104">`SetRegisters` .NET Framework sürüm 2,0 ' de uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="e232f-104">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e232f-105">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="e232f-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e232f-106">[ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md)gibi daha üst düzey işlemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e232f-106">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e232f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e232f-107">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e232f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e232f-108">Requirements</span></span>  

 <span data-ttu-id="e232f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e232f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e232f-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e232f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e232f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e232f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e232f-112">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="e232f-112">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e232f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e232f-113">See also</span></span>

- [<span data-ttu-id="e232f-114">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e232f-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="e232f-115">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e232f-115">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
