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
ms.openlocfilehash: 9f334b4a28b0573fa938c2fda340c0c03175ff18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756882"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="29564-102">ICorDebugGuidToTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29564-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="29564-103">Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgi GUID'leri harita örneği.</span><span class="sxs-lookup"><span data-stu-id="29564-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29564-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29564-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29564-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29564-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="29564-106">[in] Alınacak GUID türü eşleme nesnesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="29564-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="29564-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) nesnesini, bir Windows çalışma zamanı GUID, karşılık gelen Icordebugtype nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="29564-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="29564-108">[out] Bir işaretçi sayısına [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerçekte döndürülen nesneleri `values`.</span><span class="sxs-lookup"><span data-stu-id="29564-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29564-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29564-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29564-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29564-110">Requirements</span></span>  
 <span data-ttu-id="29564-111">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="29564-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="29564-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29564-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29564-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29564-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29564-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29564-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29564-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29564-115">See also</span></span>

- [<span data-ttu-id="29564-116">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29564-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="29564-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29564-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
