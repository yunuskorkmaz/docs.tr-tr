---
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
ms.openlocfilehash: 226b386c7a38c9a0b28b3bcc0420d14f6f4f4e7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678447"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="cecfb-102">ICorDebugThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cecfb-102">ICorDebugThreadEnum::Next Method</span></span>

<span data-ttu-id="cecfb-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugThread örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cecfb-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecfb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cecfb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cecfb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cecfb-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="cecfb-106">'ndaki `ICorDebugThread` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="cecfb-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="cecfb-107">dışı Her biri `ICorDebugThread` bir iş parçacığını temsil eden bir nesneyi işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="cecfb-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="cecfb-108">dışı `ICorDebugThread` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cecfb-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="cecfb-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="cecfb-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecfb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cecfb-110">Requirements</span></span>  

 <span data-ttu-id="cecfb-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cecfb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cecfb-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cecfb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cecfb-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cecfb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cecfb-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cecfb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
