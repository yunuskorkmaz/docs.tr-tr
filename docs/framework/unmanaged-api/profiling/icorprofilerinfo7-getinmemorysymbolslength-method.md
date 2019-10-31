---
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
ms.openlocfilehash: 299a7495d9ca9215ad21301a3ac525fa6e49a01b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130336"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="b961d-102">ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="b961d-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="b961d-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="b961d-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="b961d-104">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b961d-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b961d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b961d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b961d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b961d-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b961d-107">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="b961d-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="b961d-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="b961d-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="b961d-109">dışı Bir `DWORD` değeri işaretçisi, yöntemin döndürdüğü, akışın uzunluğunu bayt cinsinden içerir.</span><span class="sxs-lookup"><span data-stu-id="b961d-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b961d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b961d-110">Return Value</span></span>  
 <span data-ttu-id="b961d-111">Sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebilse, yöntem `S_OK` döndürür.</span><span class="sxs-lookup"><span data-stu-id="b961d-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="b961d-112">Yöntemi, yöntem <xref:System.Reflection.Emit?displayProperty=nameWithType>kullanılarak oluşturulduysa `CORPROF_E_MODULE_IS_DYNAMIC` döndürür.</span><span class="sxs-lookup"><span data-stu-id="b961d-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b961d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b961d-113">Remarks</span></span>  
 <span data-ttu-id="b961d-114">Modülün bellek içi sembolleri varsa, akışın uzunluğu `pCountSymbolBytes`yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b961d-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="b961d-115">Modülün bellek içi sembolleri yoksa, `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="b961d-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b961d-116">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="b961d-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="b961d-117">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi `CORPROF_E_MODULE_IS_DYNAMIC`döndürür.</span><span class="sxs-lookup"><span data-stu-id="b961d-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b961d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b961d-118">Requirements</span></span>  
 <span data-ttu-id="b961d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b961d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b961d-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b961d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b961d-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b961d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b961d-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b961d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b961d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b961d-123">See also</span></span>

- [<span data-ttu-id="b961d-124">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b961d-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
