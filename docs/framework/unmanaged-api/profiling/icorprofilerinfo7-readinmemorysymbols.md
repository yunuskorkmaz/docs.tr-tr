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
ms.openlocfilehash: 2a878ccf94fb4f6d67daa3a4dd42fcf98faf34a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748632"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="aedd4-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="aedd4-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="aedd4-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="aedd4-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="aedd4-104">Bayt bir bellek içi sembol akıştan okur.</span><span class="sxs-lookup"><span data-stu-id="aedd4-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedd4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aedd4-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aedd4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aedd4-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="aedd4-107">[in] Bellek içi akış içeren modül tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="aedd4-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="aedd4-108">[in] Bellek içi akış baytlar okunduktan başlayacağı içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="aedd4-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="aedd4-109">[out] Verilerin kopyalanacağı arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aedd4-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="aedd4-110">Arabellek olmalıdır `countSymbolBytes` alanı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aedd4-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="aedd4-111">[in] Kopyalanacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="aedd4-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="aedd4-112">[out] Yöntem döndürüldüğünde, okunan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="aedd4-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedd4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aedd4-113">Return Value</span></span>  
 <span data-ttu-id="aedd4-114">`S_OK`, sıfır olmayan birkaç bayt okursanız.</span><span class="sxs-lookup"><span data-stu-id="aedd4-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="aedd4-115">`CORPROF_E_MODULE_IS_DYNAMIC`, modülü kullanılarak oluşturulmuşsa <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="aedd4-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aedd4-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aedd4-116">Remarks</span></span>  
 <span data-ttu-id="aedd4-117">`ReadInMemorySymbols` Yöntemi okuma girişiminde `countSymbolBytes` uzaklıkta başlayan belirli veri `symbolsReadOffset` bellek içi akış içinde.</span><span class="sxs-lookup"><span data-stu-id="aedd4-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="aedd4-118">Verilerin kopyalanacağı `pSymbolBytes`, olması beklenen `countSymbolBytes` alanı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aedd4-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="aedd4-119">`pCountSymbolsBytesRead` Gerçek, daha az olabilir, okunan bayt sayısını içeren daha `countSymbolBytes` akışın sonuna ulaşılırsa.</span><span class="sxs-lookup"><span data-stu-id="aedd4-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aedd4-120">Geçerli uygulama Reflection.Emit desteklemez.</span><span class="sxs-lookup"><span data-stu-id="aedd4-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="aedd4-121">Modül Reflection.Emit kullanılarak oluşturulduysa, yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="aedd4-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aedd4-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aedd4-122">Requirements</span></span>  
 <span data-ttu-id="aedd4-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aedd4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedd4-124">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aedd4-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aedd4-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aedd4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aedd4-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedd4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedd4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aedd4-127">See also</span></span>

- [<span data-ttu-id="aedd4-128">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aedd4-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
