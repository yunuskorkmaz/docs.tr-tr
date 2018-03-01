---
title: "ICorDebugChainEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e78340d26e4a7ab67fa6c312b1dbd537c5c0a28c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="d3451-102">ICorDebugChainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3451-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="d3451-103">Icordebugchain örnekleri belirtilen sayıda geçerli konumdan başlayarak numaralandırması alır.</span><span class="sxs-lookup"><span data-stu-id="d3451-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3451-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3451-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3451-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3451-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d3451-106">[in] Sayısı `ICorDebugChain` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d3451-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="d3451-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugChain` zinciri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d3451-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d3451-108">[out] Sayısını gösteren bir işaretçi `ICorDebugChain` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="d3451-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="d3451-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="d3451-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3451-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3451-110">Requirements</span></span>  
 <span data-ttu-id="d3451-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3451-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3451-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3451-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3451-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3451-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3451-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3451-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
