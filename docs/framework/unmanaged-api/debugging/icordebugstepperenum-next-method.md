---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepperEnum:: Next yöntemi'
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
ms.openlocfilehash: e0c17fbc570d5ea8a4a56c89a5a2c855ed045bd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717478"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="57bf5-103">ICorDebugStepperEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57bf5-103">ICorDebugStepperEnum::Next Method</span></span>

<span data-ttu-id="57bf5-104">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugStepper örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="57bf5-104">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57bf5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57bf5-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57bf5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57bf5-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="57bf5-107">'ndaki `ICorDebugStepper` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="57bf5-107">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="57bf5-108">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugStepper` .</span><span class="sxs-lookup"><span data-stu-id="57bf5-108">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="57bf5-109">dışı `ICorDebugStepper` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57bf5-109">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="57bf5-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="57bf5-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57bf5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57bf5-111">Requirements</span></span>  

 <span data-ttu-id="57bf5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57bf5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57bf5-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57bf5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57bf5-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="57bf5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57bf5-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57bf5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
