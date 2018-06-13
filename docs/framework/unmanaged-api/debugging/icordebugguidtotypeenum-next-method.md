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
ms.openlocfilehash: c156be3af49ac99f040360bda9f60f21a9ad66b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416224"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="6471d-102">ICorDebugGuidToTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6471d-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="6471d-103">Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgilerini yazmak için GUID'leri eşleme örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6471d-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6471d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6471d-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6471d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6471d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6471d-106">[in] Alınacak GUID türünde eşleme nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="6471d-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6471d-107">[out] Her biri işaret işaretçileri, bir dizi bir [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşlemeleri nesnesi bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="6471d-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6471d-108">[out] Sayısını gösteren bir işaretçi [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerçekte döndürülen nesneleri `values`.</span><span class="sxs-lookup"><span data-stu-id="6471d-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6471d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6471d-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6471d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6471d-110">Requirements</span></span>  
 <span data-ttu-id="6471d-111">**Platform:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6471d-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="6471d-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6471d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6471d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6471d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6471d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6471d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6471d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6471d-115">See Also</span></span>  
 [<span data-ttu-id="6471d-116">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6471d-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="6471d-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6471d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
