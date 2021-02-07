---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi'
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 5d96b17e8abbd023f2d050eff3f121a871a94754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737122"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="2f559-103">ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f559-103">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>

<span data-ttu-id="2f559-104">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="2f559-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="2f559-105">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f559-105">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f559-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f559-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f559-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f559-107">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="2f559-108">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="2f559-108">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="2f559-109">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="2f559-109">pCountSymbolBytes</span></span>  
 <span data-ttu-id="2f559-110">dışı Bir değere yönelik, `DWORD` yöntemin döndürdüğü bir işaretçi, akışın uzunluğunu bayt olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="2f559-110">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f559-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f559-111">Return Value</span></span>  

 <span data-ttu-id="2f559-112">Bu yöntem, `S_OK` sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebileceği takdirde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2f559-112">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="2f559-113">Yöntemi `CORPROF_E_MODULE_IS_DYNAMIC` , yöntemi kullanılarak oluşturulduysa döndürür <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2f559-113">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f559-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f559-114">Remarks</span></span>  

 <span data-ttu-id="2f559-115">Modülün bellek içi sembolleri varsa, akışın uzunluğu içine yerleştirilir `pCountSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="2f559-115">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="2f559-116">Modülün bellek içi sembolleri yoksa `*pCountSymbolBytes = 0` .</span><span class="sxs-lookup"><span data-stu-id="2f559-116">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f559-117">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="2f559-117">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="2f559-118">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="2f559-118">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f559-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f559-119">Requirements</span></span>  

 <span data-ttu-id="2f559-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f559-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f559-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2f559-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f559-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f559-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f559-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f559-123">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f559-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f559-124">See also</span></span>

- [<span data-ttu-id="2f559-125">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f559-125">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
