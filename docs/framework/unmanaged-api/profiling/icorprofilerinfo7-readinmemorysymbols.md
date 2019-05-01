---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 662863ec69e464dafe893552f1d81755313acc75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786225"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="33b6a-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="33b6a-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="33b6a-103">[Desteklenen [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] ve sonraki sürümlerinde]</span><span class="sxs-lookup"><span data-stu-id="33b6a-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="33b6a-104">Bayt bir bellek içi sembol akıştan okur.</span><span class="sxs-lookup"><span data-stu-id="33b6a-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33b6a-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33b6a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33b6a-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="33b6a-107">[in] Bellek içi akış içeren modül tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="33b6a-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="33b6a-108">[in] Bellek içi akış baytlar okunduktan başlayacağı içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="33b6a-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="33b6a-109">[out] Verilerin kopyalanacağı arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="33b6a-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="33b6a-110">Arabellek olmalıdır `countSymbolBytes` alanı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b6a-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="33b6a-111">[in] Kopyalanacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="33b6a-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="33b6a-112">[out] Yöntem döndürüldüğünde, okunan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="33b6a-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33b6a-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="33b6a-113">Return Value</span></span>  
 <span data-ttu-id="33b6a-114">`S_OK`, sıfır olmayan birkaç bayt okursanız.</span><span class="sxs-lookup"><span data-stu-id="33b6a-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="33b6a-115">`CORPROF_E_MODULE_IS_DYNAMIC`, modülü kullanılarak oluşturulmuşsa <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="33b6a-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33b6a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33b6a-116">Remarks</span></span>  
 <span data-ttu-id="33b6a-117">`ReadInMemorySymbols` Yöntemi okuma girişiminde `countSymbolBytes` uzaklıkta başlayan belirli veri `symbolsReadOffset` bellek içi akış içinde.</span><span class="sxs-lookup"><span data-stu-id="33b6a-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="33b6a-118">Verilerin kopyalanacağı `pSymbolBytes`, olması beklenen `countSymbolBytes` alanı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b6a-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="33b6a-119">`pCountSymbolsBytesRead` Gerçek, daha az olabilir, okunan bayt sayısını içeren daha `countSymbolBytes` akışın sonuna ulaşılırsa.</span><span class="sxs-lookup"><span data-stu-id="33b6a-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33b6a-120">Geçerli uygulama Reflection.Emit desteklemez.</span><span class="sxs-lookup"><span data-stu-id="33b6a-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="33b6a-121">Modül Reflection.Emit kullanılarak oluşturulduysa, yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="33b6a-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33b6a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33b6a-122">Requirements</span></span>  
 <span data-ttu-id="33b6a-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33b6a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33b6a-124">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33b6a-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33b6a-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33b6a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33b6a-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33b6a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b6a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33b6a-127">See also</span></span>

- [<span data-ttu-id="33b6a-128">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33b6a-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
