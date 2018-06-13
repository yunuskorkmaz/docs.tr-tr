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
ms.openlocfilehash: 2f049a7cadf1857495e49b9bdc2fecd1b49103af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415489"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="8aaf3-102">ICorDebugFrameEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8aaf3-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="8aaf3-103">Icordebugframe örnekleri, geçerli konumdan başlayarak belirtilen sayıda alır.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aaf3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8aaf3-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8aaf3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8aaf3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8aaf3-106">[in] Sayısı `ICorDebugFrame` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="8aaf3-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugFrame` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8aaf3-108">[out] Sayısını gösteren bir işaretçi `ICorDebugFrame` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="8aaf3-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aaf3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8aaf3-110">Requirements</span></span>  
 <span data-ttu-id="8aaf3-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aaf3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aaf3-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aaf3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aaf3-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aaf3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aaf3-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aaf3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
