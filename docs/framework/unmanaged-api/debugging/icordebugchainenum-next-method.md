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
ms.openlocfilehash: 2d075820df534e08bdf4c2b75d36f6a60f979662
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894090"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="b6a54-102">ICorDebugChainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6a54-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="b6a54-103">Geçerli konumdan başlayarak sabit listesinden belirtilen ıcordebugzincirine örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b6a54-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6a54-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6a54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6a54-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b6a54-106">'ndaki Alınacak `ICorDebugChain` örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6a54-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="b6a54-107">dışı Her biri zinciri temsil eden bir `ICorDebugChain` nesneyi işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6a54-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b6a54-108">dışı Aslında döndürülen `ICorDebugChain` örnek sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6a54-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="b6a54-109">Bu değer bir `celt` ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6a54-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6a54-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6a54-110">Requirements</span></span>  
 <span data-ttu-id="b6a54-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6a54-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a54-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6a54-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6a54-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b6a54-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6a54-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6a54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
