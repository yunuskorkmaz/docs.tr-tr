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
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210390"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="1c52a-102">ICorDebugILCode::GetEHClauses Metodu</span><span class="sxs-lookup"><span data-stu-id="1c52a-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="1c52a-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="1c52a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1c52a-104">Bu ara dil (IL) için tanımlanan özel durum işleme (EH) yan tümceleri listesine yönelik bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c52a-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c52a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c52a-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c52a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c52a-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="1c52a-107">'ndaki Dizinin depolama kapasitesi `clauses` .</span><span class="sxs-lookup"><span data-stu-id="1c52a-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="1c52a-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1c52a-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="1c52a-109">dışı Hangi bilgilerin diziye yazıldığı hakkında yan tümceler sayısı `clauses` .</span><span class="sxs-lookup"><span data-stu-id="1c52a-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="1c52a-110">yan</span><span class="sxs-lookup"><span data-stu-id="1c52a-110">clauses</span></span>  
 <span data-ttu-id="1c52a-111">dışı Bu Il için tanımlanan özel durum işleme yan tümceleri hakkında bilgi içeren bir [corhata ayıklama Gehclause](cordebugehclause-structure.md) nesneleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="1c52a-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c52a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c52a-112">Remarks</span></span>  
 <span data-ttu-id="1c52a-113">`cClauses`0 ise ve `pcClauses` **null**değilse, `pcClauses` kullanılabilir özel durum işleme yan tümceleri sayısına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1c52a-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="1c52a-114">`cClauses`Sıfır olmayan ise, dizinin depolama kapasitesini temsil eder `clauses` .</span><span class="sxs-lookup"><span data-stu-id="1c52a-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="1c52a-115">Yöntemi döndürüldüğünde, `clauses` en fazla `cClauses` öğe içerir ve `pcClauses` gerçekten diziye yazılan yan tümce sayısına ayarlanır `clauses` .</span><span class="sxs-lookup"><span data-stu-id="1c52a-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c52a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c52a-116">Requirements</span></span>  
 <span data-ttu-id="1c52a-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c52a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c52a-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c52a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c52a-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1c52a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c52a-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c52a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c52a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c52a-121">See also</span></span>

- [<span data-ttu-id="1c52a-122">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c52a-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="1c52a-123">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="1c52a-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="1c52a-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1c52a-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
