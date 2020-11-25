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
ms.openlocfilehash: 0f42020821ec71d1e59ae8097f22ee530e16a576
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706183"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="6af2f-102">ICorDebugChainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6af2f-102">ICorDebugChainEnum::Next Method</span></span>

<span data-ttu-id="6af2f-103">Geçerli konumdan başlayarak sabit listesinden belirtilen ıcordebugzincirine örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6af2f-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af2f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6af2f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af2f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6af2f-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="6af2f-106">'ndaki `ICorDebugChain` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="6af2f-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="6af2f-107">dışı Her biri zinciri temsil eden bir nesneyi işaret eden işaretçiler dizisi `ICorDebugChain` .</span><span class="sxs-lookup"><span data-stu-id="6af2f-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6af2f-108">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugChain` .</span><span class="sxs-lookup"><span data-stu-id="6af2f-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="6af2f-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="6af2f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af2f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6af2f-110">Requirements</span></span>  

 <span data-ttu-id="6af2f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6af2f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af2f-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6af2f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6af2f-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6af2f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6af2f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af2f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
