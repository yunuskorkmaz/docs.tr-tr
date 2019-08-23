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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157b0e215f8afa58cccb3d54a65baa9c307ba966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955421"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="25837-102">ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="25837-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="25837-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="25837-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="25837-104">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="25837-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25837-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25837-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25837-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25837-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="25837-107">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="25837-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="25837-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="25837-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="25837-109">dışı Bir `DWORD` değere yönelik, yöntemin döndürdüğü bir işaretçi, akışın uzunluğunu bayt olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="25837-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25837-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25837-110">Return Value</span></span>  
 <span data-ttu-id="25837-111">Bu yöntem, `S_OK` sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebileceği takdirde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25837-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="25837-112">Yöntemi, yöntemi `CORPROF_E_MODULE_IS_DYNAMIC` kullanılarak <xref:System.Reflection.Emit?displayProperty=nameWithType>oluşturulduysa döndürür.</span><span class="sxs-lookup"><span data-stu-id="25837-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25837-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25837-113">Remarks</span></span>  
 <span data-ttu-id="25837-114">Modülün bellek içi sembolleri varsa, akışın uzunluğu içine `pCountSymbolBytes`yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="25837-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="25837-115">Modülün bellek içi sembolleri `*pCountSymbolBytes = 0`yoksa.</span><span class="sxs-lookup"><span data-stu-id="25837-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25837-116">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="25837-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="25837-117">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="25837-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25837-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25837-118">Requirements</span></span>  
 <span data-ttu-id="25837-119">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25837-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25837-120">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="25837-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25837-121">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="25837-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25837-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25837-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25837-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25837-123">See also</span></span>

- [<span data-ttu-id="25837-124">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25837-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
