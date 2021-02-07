---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugChainEnum:: Next yöntemi'
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
ms.openlocfilehash: 5ab6665eb5af6d9f145f9aab67aeb75b4769e7e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711576"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="54207-103">ICorDebugChainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54207-103">ICorDebugChainEnum::Next Method</span></span>

<span data-ttu-id="54207-104">Geçerli konumdan başlayarak sabit listesinden belirtilen ıcordebugzincirine örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="54207-104">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54207-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54207-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54207-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54207-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="54207-107">'ndaki `ICorDebugChain` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="54207-107">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="54207-108">dışı Her biri zinciri temsil eden bir nesneyi işaret eden işaretçiler dizisi `ICorDebugChain` .</span><span class="sxs-lookup"><span data-stu-id="54207-108">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="54207-109">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugChain` .</span><span class="sxs-lookup"><span data-stu-id="54207-109">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="54207-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="54207-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54207-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54207-111">Requirements</span></span>  

 <span data-ttu-id="54207-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54207-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54207-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54207-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54207-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="54207-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54207-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54207-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
