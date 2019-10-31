---
title: ICorDebugObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: adcfbf1207ad7895ab55f7e5cf9581905cb826bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096102"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="4b685-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b685-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="4b685-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen nesne sayısının göreli sanal adreslerini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="4b685-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b685-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b685-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b685-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b685-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4b685-106">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="4b685-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="4b685-107">dışı Her biri bir CORDB_ADDRESS nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="4b685-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4b685-108">dışı Gerçekten döndürülen nesne sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4b685-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="4b685-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b685-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b685-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b685-110">Requirements</span></span>  
 <span data-ttu-id="4b685-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b685-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b685-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b685-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b685-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4b685-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b685-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b685-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b685-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b685-115">See also</span></span>
