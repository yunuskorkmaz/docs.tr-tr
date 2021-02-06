---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThreadEnum:: Next yöntemi'
title: ICorDebugThreadEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 2cfb651d65eaf0f5797444ea1bec587cebdde2f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658431"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="c2c68-103">ICorDebugThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2c68-103">ICorDebugThreadEnum::Next Method</span></span>

<span data-ttu-id="c2c68-104">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugThread örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c2c68-104">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2c68-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2c68-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="c2c68-107">'ndaki `ICorDebugThread` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="c2c68-107">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="c2c68-108">dışı Her biri `ICorDebugThread` bir iş parçacığını temsil eden bir nesneyi işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="c2c68-108">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c2c68-109">dışı `ICorDebugThread` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c2c68-109">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="c2c68-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="c2c68-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c68-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2c68-111">Requirements</span></span>  

 <span data-ttu-id="c2c68-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c68-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c68-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2c68-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2c68-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c2c68-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c68-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c68-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
