---
title: 'ICorProfilerInfo7:: ReadInMemorySymbols'
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
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955370"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="87ec3-102">ICorProfilerInfo7:: ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="87ec3-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="87ec3-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="87ec3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="87ec3-104">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="87ec3-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ec3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87ec3-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ec3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87ec3-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="87ec3-107">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="87ec3-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="87ec3-108">'ndaki Bayt okumaya başlamak için bellek içi akış içindeki fark.</span><span class="sxs-lookup"><span data-stu-id="87ec3-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="87ec3-109">dışı Verilerin kopyalanacağı arabelleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87ec3-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="87ec3-110">Arabellekte kullanılabilir alan olması `countSymbolBytes` gerekir.</span><span class="sxs-lookup"><span data-stu-id="87ec3-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="87ec3-111">'ndaki Kopyalanacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="87ec3-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="87ec3-112">dışı Yöntemi döndüğünde, okunan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="87ec3-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87ec3-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87ec3-113">Return Value</span></span>  
 <span data-ttu-id="87ec3-114">`S_OK`sıfır olmayan bir bayt miktarı okundum.</span><span class="sxs-lookup"><span data-stu-id="87ec3-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="87ec3-115">`CORPROF_E_MODULE_IS_DYNAMIC`, modül kullanılarak <xref:System.Reflection.Emit>oluşturulduysa.</span><span class="sxs-lookup"><span data-stu-id="87ec3-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ec3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87ec3-116">Remarks</span></span>  
 <span data-ttu-id="87ec3-117">Yöntemi `ReadInMemorySymbols` , bellek içi akış `countSymbolBytes` içinde uzaklığında `symbolsReadOffset` başlayarak verileri okumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="87ec3-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="87ec3-118">Veriler, kullanılabilir alan olması `pSymbolBytes` `countSymbolBytes` beklenen öğesine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="87ec3-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="87ec3-119">`pCountSymbolsBytesRead`okunan toplam bayt sayısını içerir, bu da akışın sonuna ulaşılırsa daha `countSymbolBytes` az olabilir.</span><span class="sxs-lookup"><span data-stu-id="87ec3-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87ec3-120">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="87ec3-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="87ec3-121">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="87ec3-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ec3-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87ec3-122">Requirements</span></span>  
 <span data-ttu-id="87ec3-123">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ec3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ec3-124">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87ec3-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87ec3-125">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87ec3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87ec3-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ec3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ec3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87ec3-127">See also</span></span>

- [<span data-ttu-id="87ec3-128">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ec3-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
