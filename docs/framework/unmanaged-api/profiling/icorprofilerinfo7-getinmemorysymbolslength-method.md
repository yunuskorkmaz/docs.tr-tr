---
title: ICorProfilerInfo7::GetInMemorySymbolsLength yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422fdfef6bea40e0f4bcc7447df8dba1eab2896e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919093"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="8f8ea-102">ICorProfilerInfo7::GetInMemorySymbolsLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f8ea-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="8f8ea-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="8f8ea-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8f8ea-104">Bir bellek içi sembol akış uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f8ea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f8ea-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f8ea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f8ea-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8f8ea-107">[in] Bellek içi akış içeren modül tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="8f8ea-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="8f8ea-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="8f8ea-109">[out] Bir işaretçi bir `DWORD` yöntem döndürüldüğünde, akış bayt cinsinden uzunluğunu içeren bir değer.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f8ea-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f8ea-110">Return Value</span></span>  
 <span data-ttu-id="8f8ea-111">Yöntem döndürür `S_OK` sıfır (0) olsa bile bellek akışının uzunluğu, belirlenebilir durumunda.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="8f8ea-112">Yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC` yöntemi kullanılarak oluşturulmuşsa <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f8ea-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f8ea-113">Remarks</span></span>  
 <span data-ttu-id="8f8ea-114">Modül bellek içi simgeleri varsa, akışın uzunluğu yerleştirildi `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="8f8ea-115">Bellek içi sembolleri modülü yoksa `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f8ea-116">Geçerli uygulama Reflection.Emit desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="8f8ea-117">Modül Reflection.Emit kullanılarak oluşturulduysa, yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f8ea-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f8ea-118">Requirements</span></span>  
 <span data-ttu-id="8f8ea-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f8ea-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8ea-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f8ea-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f8ea-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f8ea-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f8ea-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f8ea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8ea-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f8ea-123">See also</span></span>

- [<span data-ttu-id="8f8ea-124">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f8ea-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
