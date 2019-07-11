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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9be126e45d8428d8786e9aadf2195133d1957440
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754825"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="f6a25-102">ICorDebugFrameEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6a25-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="f6a25-103">Icordebugframe örnekleri, geçerli konumdan başlayarak belirtilen sayıda alır.</span><span class="sxs-lookup"><span data-stu-id="f6a25-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6a25-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6a25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6a25-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f6a25-106">[in] Sayısını `ICorDebugFrame` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f6a25-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="f6a25-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="f6a25-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f6a25-108">[out] Bir işaretçi sayısına `ICorDebugFrame` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f6a25-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="f6a25-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="f6a25-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6a25-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6a25-110">Requirements</span></span>  
 <span data-ttu-id="f6a25-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6a25-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6a25-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6a25-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6a25-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6a25-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6a25-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6a25-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
