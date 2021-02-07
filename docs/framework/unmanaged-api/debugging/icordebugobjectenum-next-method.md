---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugObjectEnum:: Next yöntemi'
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
ms.openlocfilehash: dd7d4240827e14962edf7573b59b273f65231bcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729048"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="ea709-103">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea709-103">ICorDebugObjectEnum::Next Method</span></span>

<span data-ttu-id="ea709-104">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen nesne sayısının göreli sanal adreslerini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="ea709-104">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea709-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea709-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea709-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea709-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ea709-107">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="ea709-107">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="ea709-108">dışı Her biri bir CORDB_ADDRESS nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ea709-108">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ea709-109">dışı Gerçekten döndürülen nesne sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea709-109">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="ea709-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="ea709-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea709-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea709-111">Requirements</span></span>  

 <span data-ttu-id="ea709-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea709-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea709-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea709-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea709-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea709-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea709-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea709-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea709-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea709-116">See also</span></span>
