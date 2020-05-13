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
ms.openlocfilehash: 70514464f27d6123a4de1d5800ed016a39541287
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207550"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="6d4d8-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d4d8-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="6d4d8-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen nesne sayısının göreli sanal adreslerini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="6d4d8-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d4d8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d4d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d4d8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6d4d8-106">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="6d4d8-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6d4d8-107">dışı Her biri bir CORDB_ADDRESS nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="6d4d8-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6d4d8-108">dışı Gerçekten döndürülen nesne sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d4d8-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="6d4d8-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="6d4d8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d4d8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d4d8-110">Requirements</span></span>  
 <span data-ttu-id="6d4d8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d4d8-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d4d8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d4d8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d4d8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d4d8-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d4d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4d8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d4d8-115">See also</span></span>
