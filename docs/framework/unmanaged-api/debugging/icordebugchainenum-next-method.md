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
ms.openlocfilehash: cd4f27b958aa4b25c2662d8a5e9da6bcdc73d5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404462"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="eb890-102">ICorDebugChainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb890-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="eb890-103">Icordebugchain örnekleri belirtilen sayıda geçerli konumdan başlayarak numaralandırması alır.</span><span class="sxs-lookup"><span data-stu-id="eb890-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb890-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb890-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb890-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb890-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="eb890-106">[in] Sayısı `ICorDebugChain` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="eb890-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="eb890-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugChain` zinciri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="eb890-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="eb890-108">[out] Sayısını gösteren bir işaretçi `ICorDebugChain` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="eb890-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="eb890-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="eb890-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb890-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb890-110">Requirements</span></span>  
 <span data-ttu-id="eb890-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb890-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb890-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb890-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb890-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb890-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb890-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb890-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
