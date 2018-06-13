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
ms.openlocfilehash: 59b37c30df6467439d04e367e13b0fc4ffff0ec6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422952"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="fe962-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe962-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="fe962-103">Geçerli konumdan başlayarak numaralandırması nesneleri belirtilen sayıdaki göreli sanal adresleri (RVAs) alır.</span><span class="sxs-lookup"><span data-stu-id="fe962-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe962-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe962-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe962-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe962-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fe962-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="fe962-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="fe962-107">[out] Her biri bir CORDB_ADDRESS nesnesine işaret eden bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fe962-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fe962-108">[out] İşaretçi gerçekte döndürülen nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="fe962-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="fe962-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="fe962-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe962-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe962-110">Requirements</span></span>  
 <span data-ttu-id="fe962-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe962-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe962-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe962-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe962-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe962-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe962-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe962-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe962-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe962-115">See Also</span></span>  
 
