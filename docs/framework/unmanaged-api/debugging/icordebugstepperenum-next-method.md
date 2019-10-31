---
title: ICorDebugStepperEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: 11d9c7393827b613d49e23972b4896bfe657a544
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138982"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="0d7e1-102">ICorDebugStepperEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d7e1-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="0d7e1-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugStepper örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0d7e1-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d7e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d7e1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d7e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d7e1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0d7e1-106">'ndaki Alınacak `ICorDebugStepper` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0d7e1-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="0d7e1-107">dışı Her biri bir `ICorDebugStepper` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0d7e1-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0d7e1-108">dışı Aslında döndürülen `ICorDebugStepper` örneklerinin sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d7e1-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="0d7e1-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d7e1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d7e1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d7e1-110">Requirements</span></span>  
 <span data-ttu-id="0d7e1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d7e1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d7e1-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d7e1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d7e1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0d7e1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d7e1-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d7e1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
