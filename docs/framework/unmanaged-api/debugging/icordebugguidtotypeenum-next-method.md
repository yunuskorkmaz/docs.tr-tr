---
title: "ICorDebugGuidToTypeEnum::Next Yöntemi"
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
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3bcfbcfb85fc5eb1d58142af4e7d825162e9861b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="5d481-102">ICorDebugGuidToTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d481-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="5d481-103">Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgilerini yazmak için GUID'leri eşleme örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5d481-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d481-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d481-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d481-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d481-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5d481-106">[in] Alınacak GUID türünde eşleme nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d481-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="5d481-107">[out] Her biri işaret işaretçileri, bir dizi bir [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşlemeleri nesnesi bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="5d481-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5d481-108">[out] Sayısını gösteren bir işaretçi [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerçekte döndürülen nesneleri `values`.</span><span class="sxs-lookup"><span data-stu-id="5d481-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d481-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d481-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d481-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d481-110">Requirements</span></span>  
 <span data-ttu-id="5d481-111">**Platformlar:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d481-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="5d481-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d481-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d481-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d481-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d481-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d481-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d481-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d481-115">See Also</span></span>  
 [<span data-ttu-id="5d481-116">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d481-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="5d481-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d481-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
