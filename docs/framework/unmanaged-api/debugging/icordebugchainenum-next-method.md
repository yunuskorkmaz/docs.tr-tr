---
title: ICorDebugChainEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26df40297d080d1ccc9464f7b09e7731f135e270
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489832"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="8ef9f-102">ICorDebugChainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ef9f-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="8ef9f-103">Geçerli konumunda başlayan bir numaralandırma Icordebugchain örneği belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8ef9f-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef9f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ef9f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef9f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ef9f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8ef9f-106">[in] Sayısını `ICorDebugChain` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8ef9f-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="8ef9f-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugChain` zinciri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="8ef9f-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8ef9f-108">[out] Bir işaretçi sayısına `ICorDebugChain` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8ef9f-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="8ef9f-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="8ef9f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef9f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ef9f-110">Requirements</span></span>  
 <span data-ttu-id="8ef9f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef9f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef9f-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ef9f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ef9f-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef9f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ef9f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef9f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
