---
description: ': ICorProfilerInfo7:: ReadInMemorySymbols hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7f1a88d823e7cdfcc89aa140681f61cfbe3f63ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736992"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="3aff7-103">ICorProfilerInfo7:: ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="3aff7-103">ICorProfilerInfo7::ReadInMemorySymbols</span></span>

<span data-ttu-id="3aff7-104">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="3aff7-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3aff7-105">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="3aff7-105">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aff7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aff7-106">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aff7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3aff7-107">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="3aff7-108">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="3aff7-108">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="3aff7-109">'ndaki Bayt okumaya başlamak için bellek içi akış içindeki fark.</span><span class="sxs-lookup"><span data-stu-id="3aff7-109">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="3aff7-110">dışı Verilerin kopyalanacağı arabelleğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3aff7-110">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="3aff7-111">Arabellekte `countSymbolBytes` kullanılabilir alan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3aff7-111">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="3aff7-112">'ndaki Kopyalanacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3aff7-112">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="3aff7-113">dışı Yöntemi döndüğünde, okunan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="3aff7-113">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aff7-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3aff7-114">Return Value</span></span>  

 <span data-ttu-id="3aff7-115">`S_OK`sıfır olmayan bir bayt miktarı okundum.</span><span class="sxs-lookup"><span data-stu-id="3aff7-115">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="3aff7-116">`CORPROF_E_MODULE_IS_DYNAMIC`, modül kullanılarak oluşturulduysa <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="3aff7-116">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aff7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aff7-117">Remarks</span></span>  

 <span data-ttu-id="3aff7-118">`ReadInMemorySymbols`Yöntemi, `countSymbolBytes` `symbolsReadOffset` bellek içi akış içinde uzaklığında başlayarak verileri okumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="3aff7-118">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="3aff7-119">Veriler `pSymbolBytes` , kullanılabilir alan olması beklenen öğesine kopyalanır `countSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="3aff7-119">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="3aff7-120">`pCountSymbolsBytesRead` okunan toplam bayt sayısını içerir, bu da `countSymbolBytes` akışın sonuna ulaşılırsa daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="3aff7-120">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3aff7-121">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="3aff7-121">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="3aff7-122">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="3aff7-122">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aff7-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3aff7-123">Requirements</span></span>  

 <span data-ttu-id="3aff7-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aff7-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aff7-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3aff7-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3aff7-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3aff7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3aff7-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aff7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aff7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aff7-128">See also</span></span>

- [<span data-ttu-id="3aff7-129">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3aff7-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
