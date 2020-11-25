---
title: ICorDebugFrameEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 76b96dfd9d22c7e770671dcc01cb421430df729f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728192"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="a6e6a-102">ICorDebugFrameEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6e6a-102">ICorDebugFrameEnum::Next Method</span></span>

<span data-ttu-id="a6e6a-103">Geçerli konumdan başlayarak, belirtilen ICorDebugFrame örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a6e6a-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e6a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a6e6a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6e6a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6e6a-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="a6e6a-106">'ndaki `ICorDebugFrame` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="a6e6a-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="a6e6a-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="a6e6a-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a6e6a-108">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="a6e6a-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="a6e6a-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="a6e6a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6e6a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6e6a-110">Requirements</span></span>  

 <span data-ttu-id="a6e6a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6e6a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6e6a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6e6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6e6a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a6e6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6e6a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
