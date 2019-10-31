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
ms.openlocfilehash: ff74a9849b74b8a8e6b8c03f1fc4e7c7eee1ec14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124055"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="1abd0-102">ICorDebugFrameEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1abd0-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="1abd0-103">Geçerli konumdan başlayarak, belirtilen ICorDebugFrame örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1abd0-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abd0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1abd0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1abd0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1abd0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1abd0-106">'ndaki Alınacak `ICorDebugFrame` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="1abd0-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="1abd0-107">dışı Her biri bir `ICorDebugFrame` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="1abd0-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1abd0-108">dışı Gerçekten döndürülen `ICorDebugFrame` örneklerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1abd0-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="1abd0-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="1abd0-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1abd0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1abd0-110">Requirements</span></span>  
 <span data-ttu-id="1abd0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1abd0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1abd0-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1abd0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1abd0-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1abd0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1abd0-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1abd0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
