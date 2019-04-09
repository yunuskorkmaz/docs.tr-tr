---
title: ICorDebugGuidToTypeEnum::Next Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f48c142b2b3742d01a8f796f11d5c9174529a041
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105832"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="946a9-102">ICorDebugGuidToTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="946a9-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="946a9-103">Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgi GUID'leri harita örneği.</span><span class="sxs-lookup"><span data-stu-id="946a9-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="946a9-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="946a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="946a9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="946a9-106">[in] Alınacak GUID türü eşleme nesnesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="946a9-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="946a9-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşleyen nesne bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="946a9-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="946a9-108">[out] Bir işaretçi sayısına [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerçekte döndürülen nesneleri `values`.</span><span class="sxs-lookup"><span data-stu-id="946a9-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="946a9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="946a9-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946a9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="946a9-110">Requirements</span></span>  
 **<span data-ttu-id="946a9-111">Platformlar:</span><span class="sxs-lookup"><span data-stu-id="946a9-111">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="946a9-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="946a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="946a9-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="946a9-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="946a9-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="946a9-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="946a9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="946a9-115">See also</span></span>

- [<span data-ttu-id="946a9-116">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="946a9-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="946a9-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="946a9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
