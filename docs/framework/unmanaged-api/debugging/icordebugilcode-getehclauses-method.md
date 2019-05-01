---
title: ICorDebugILCode::GetEHClauses Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995559"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="9962f-102">ICorDebugILCode::GetEHClauses Metodu</span><span class="sxs-lookup"><span data-stu-id="9962f-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="9962f-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="9962f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9962f-104">Özel durum işleme bu Ara dil (IL) için tanımlanan (EH) yan tümceleri listesine bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9962f-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9962f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9962f-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9962f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9962f-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="9962f-107">[in] Depolama kapasitesini `clauses` dizisi.</span><span class="sxs-lookup"><span data-stu-id="9962f-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="9962f-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9962f-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="9962f-109">[out] Hangi bilgilerin yazıldığını için yan tümceler sayısını `clauses` dizisi.</span><span class="sxs-lookup"><span data-stu-id="9962f-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="9962f-110">Yan tümceleri</span><span class="sxs-lookup"><span data-stu-id="9962f-110">clauses</span></span>  
 <span data-ttu-id="9962f-111">[out] Bir dizi [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) özel durum işleme için bu IL tanımlanan yan tümceleri hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="9962f-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9962f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9962f-112">Remarks</span></span>  
 <span data-ttu-id="9962f-113">Varsa `cClauses` 0'dır ve `pcClauses` olan olmayan**null**, `pcClauses` kullanılabilir özel durum yan tümceleri işleme sayısını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9962f-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="9962f-114">Varsa `cClauses` sıfır olan depolama kapasitesini temsil ettiği `clauses` dizisi.</span><span class="sxs-lookup"><span data-stu-id="9962f-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="9962f-115">Yöntem döndürüldüğünde `clauses` en çok içeren `cClauses` öğeleri ve `pcClauses` gerçekte yazılan yan tümceleri sayısına ayarlayın `clauses` dizisi.</span><span class="sxs-lookup"><span data-stu-id="9962f-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9962f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9962f-116">Requirements</span></span>  
 <span data-ttu-id="9962f-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9962f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9962f-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9962f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9962f-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9962f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9962f-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9962f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9962f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9962f-121">See also</span></span>

- [<span data-ttu-id="9962f-122">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9962f-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="9962f-123">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="9962f-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="9962f-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9962f-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
