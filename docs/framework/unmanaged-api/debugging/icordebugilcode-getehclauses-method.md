---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugilcode:: Getehtümceleri yöntemi'
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
ms.openlocfilehash: e790f0f1f69a38d3a1be9e98eacfc5e37be0fd05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660667"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="f5adc-103">ICorDebugILCode::GetEHClauses Metodu</span><span class="sxs-lookup"><span data-stu-id="f5adc-103">ICorDebugILCode::GetEHClauses Method</span></span>

<span data-ttu-id="f5adc-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="f5adc-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f5adc-105">Bu ara dil (IL) için tanımlanan özel durum işleme (EH) yan tümceleri listesine yönelik bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5adc-105">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5adc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5adc-106">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5adc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5adc-107">Parameters</span></span>  

 `cClauses`  
 <span data-ttu-id="f5adc-108">'ndaki Dizinin depolama kapasitesi `clauses` .</span><span class="sxs-lookup"><span data-stu-id="f5adc-108">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="f5adc-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f5adc-109">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="f5adc-110">dışı Hangi bilgilerin diziye yazıldığı hakkında yan tümceler sayısı `clauses` .</span><span class="sxs-lookup"><span data-stu-id="f5adc-110">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="f5adc-111">yan</span><span class="sxs-lookup"><span data-stu-id="f5adc-111">clauses</span></span>  
 <span data-ttu-id="f5adc-112">dışı Bu Il için tanımlanan özel durum işleme yan tümceleri hakkında bilgi içeren bir [corhata ayıklama Gehclause](cordebugehclause-structure.md) nesneleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="f5adc-112">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5adc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5adc-113">Remarks</span></span>  

 <span data-ttu-id="f5adc-114">`cClauses`0 ise ve `pcClauses` **null** değilse, `pcClauses` kullanılabilir özel durum işleme yan tümceleri sayısına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f5adc-114">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="f5adc-115">`cClauses`Sıfır olmayan ise, dizinin depolama kapasitesini temsil eder `clauses` .</span><span class="sxs-lookup"><span data-stu-id="f5adc-115">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="f5adc-116">Yöntemi döndürüldüğünde, `clauses` en fazla `cClauses` öğe içerir ve `pcClauses` gerçekten diziye yazılan yan tümce sayısına ayarlanır `clauses` .</span><span class="sxs-lookup"><span data-stu-id="f5adc-116">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5adc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5adc-117">Requirements</span></span>  

 <span data-ttu-id="f5adc-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5adc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5adc-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5adc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5adc-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5adc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5adc-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5adc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5adc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5adc-122">See also</span></span>

- [<span data-ttu-id="f5adc-123">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5adc-123">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="f5adc-124">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="f5adc-124">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="f5adc-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5adc-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
