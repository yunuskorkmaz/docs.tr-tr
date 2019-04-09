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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6998be3daf0ab6a6290a3400b96c32227df3e022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175103"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="b8114-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8114-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="b8114-103">Geçerli konumunda başlayan sabit listesi, belirli sayıda nesneleri, göreli sanal adreslerine (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="b8114-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8114-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8114-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8114-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8114-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b8114-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="b8114-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="b8114-107">[out] Bir dizi işaretçileri, her biri bir CORDB_ADDRESS nesneye işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b8114-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b8114-108">[out] Gerçekte döndürülen nesne sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b8114-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="b8114-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="b8114-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8114-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8114-110">Requirements</span></span>  
 <span data-ttu-id="b8114-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8114-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8114-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8114-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8114-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8114-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b8114-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b8114-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8114-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8114-115">See also</span></span>
