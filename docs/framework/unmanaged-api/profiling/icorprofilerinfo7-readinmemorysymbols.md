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
ms.openlocfilehash: 6732457220d795bbf8ae54277ef9f5c07cf96359
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495365"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="7e844-102">ICorProfilerInfo7:: ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="7e844-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="7e844-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="7e844-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="7e844-104">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="7e844-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e844-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e844-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e844-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e844-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7e844-107">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="7e844-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="7e844-108">'ndaki Bayt okumaya başlamak için bellek içi akış içindeki fark.</span><span class="sxs-lookup"><span data-stu-id="7e844-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="7e844-109">dışı Verilerin kopyalanacağı arabelleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7e844-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="7e844-110">Arabellekte `countSymbolBytes` kullanılabilir alan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e844-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="7e844-111">'ndaki Kopyalanacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7e844-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="7e844-112">dışı Yöntemi döndüğünde, okunan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="7e844-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e844-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7e844-113">Return Value</span></span>  
 <span data-ttu-id="7e844-114">`S_OK`sıfır olmayan bir bayt miktarı okundum.</span><span class="sxs-lookup"><span data-stu-id="7e844-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="7e844-115">`CORPROF_E_MODULE_IS_DYNAMIC`, modül kullanılarak oluşturulduysa <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="7e844-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e844-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e844-116">Remarks</span></span>  
 <span data-ttu-id="7e844-117">`ReadInMemorySymbols`Yöntemi, `countSymbolBytes` `symbolsReadOffset` bellek içi akış içinde uzaklığında başlayarak verileri okumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e844-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="7e844-118">Veriler `pSymbolBytes` , kullanılabilir alan olması beklenen öğesine kopyalanır `countSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="7e844-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="7e844-119">`pCountSymbolsBytesRead`okunan toplam bayt sayısını içerir, bu da `countSymbolBytes` akışın sonuna ulaşılırsa daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e844-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e844-120">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="7e844-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="7e844-121">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="7e844-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e844-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e844-122">Requirements</span></span>  
 <span data-ttu-id="7e844-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e844-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e844-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7e844-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e844-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e844-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e844-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e844-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e844-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e844-127">See also</span></span>

- [<span data-ttu-id="7e844-128">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e844-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
