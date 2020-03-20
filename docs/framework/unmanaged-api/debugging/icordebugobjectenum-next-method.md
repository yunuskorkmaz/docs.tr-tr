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
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178697"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="9d154-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d154-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="9d154-103">Geçerli konumdan başlayarak, belirtilen nesne sayısının göreli sanal adreslerini (RVAs) numaralandırmadan alır.</span><span class="sxs-lookup"><span data-stu-id="9d154-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d154-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d154-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d154-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d154-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9d154-106">[içinde] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="9d154-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9d154-107">[çıkış] Her biri CORDB_ADDRESS bir nesneyi işaret eden bir dizi işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d154-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9d154-108">[çıkış] Gerçekte döndürülen nesne sayısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d154-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="9d154-109">Bu değer, varsa `celt` null olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d154-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d154-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d154-110">Requirements</span></span>  
 <span data-ttu-id="9d154-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d154-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d154-112">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d154-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d154-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d154-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d154-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d154-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d154-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d154-115">See also</span></span>
