---
title: ICorProfilerModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc33936735c40e2f30189066d80444b9fcb075ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671895"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="d1ce2-102">ICorProfilerModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1ce2-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="d1ce2-103">Belirtilen bitişik modül sayısı dizideki geçerli konum Numaralandırıcının başlayarak modüllerinin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ce2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1ce2-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1ce2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1ce2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d1ce2-106">[in] Alınacak modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="d1ce2-107">[out] Bir dizi `ModuleID` değerler, her biri alınan bir modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d1ce2-108">[out] Gerçekte döndürülen öğe sayısına bir işaretçi `ids` dizisi.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1ce2-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1ce2-109">Return Value</span></span>  
 <span data-ttu-id="d1ce2-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d1ce2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1ce2-111">HRESULT</span></span>|<span data-ttu-id="d1ce2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1ce2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1ce2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1ce2-113">S_OK</span></span>|<span data-ttu-id="d1ce2-114">`celt` öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="d1ce2-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d1ce2-115">S_FALSE</span></span>|<span data-ttu-id="d1ce2-116">Az `celt` öğeleri döndürüldü, numaralandırma tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1ce2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1ce2-117">Requirements</span></span>  
 <span data-ttu-id="d1ce2-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1ce2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1ce2-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1ce2-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1ce2-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1ce2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1ce2-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1ce2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ce2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1ce2-122">See also</span></span>
- [<span data-ttu-id="d1ce2-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1ce2-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="d1ce2-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d1ce2-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
