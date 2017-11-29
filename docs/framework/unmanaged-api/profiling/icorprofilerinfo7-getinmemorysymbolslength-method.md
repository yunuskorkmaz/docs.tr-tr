---
title: "ICorProfilerInfo7::GetInMemorySymbolsLength yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type: COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34da00bdc33a836e5f459e6e4314f252e1e39e9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="46265-102">ICorProfilerInfo7::GetInMemorySymbolsLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="46265-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="46265-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="46265-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="46265-104">Bellek içi simgesi akış uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="46265-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46265-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46265-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46265-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46265-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="46265-107">[in] Bellek içi akış içeren modül tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="46265-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="46265-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="46265-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="46265-109">[out] Bir işaretçi bir `DWORD` yöntem döndürüldüğünde, akış bayt cinsinden uzunluğu değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="46265-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46265-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="46265-110">Return Value</span></span>  
 <span data-ttu-id="46265-111">Yöntem `S_OK` sıfır (0) olsa bile bellek akış uzunluğu, belirlenebilir durumunda.</span><span class="sxs-lookup"><span data-stu-id="46265-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="46265-112">Yöntem `CORPROF_E_MODULE_IS_DYNAMIC` yöntemi kullanılarak oluşturulduysa <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46265-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46265-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46265-113">Remarks</span></span>  
 <span data-ttu-id="46265-114">Modül bellek içi simgeleri varsa, akış uzunluğu yerleştirilir `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="46265-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="46265-115">Bellek içi simgeleri modülü yoksa `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="46265-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46265-116">Geçerli uygulama Reflection.Emit desteklemez.</span><span class="sxs-lookup"><span data-stu-id="46265-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="46265-117">Modül Reflection.Emit kullanılarak oluşturulup oluşturulmadığını, yöntem `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="46265-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46265-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46265-118">Requirements</span></span>  
 <span data-ttu-id="46265-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46265-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46265-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46265-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46265-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46265-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46265-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46265-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46265-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46265-123">See Also</span></span>  
 [<span data-ttu-id="46265-124">ICorProfilerInfo7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="46265-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
