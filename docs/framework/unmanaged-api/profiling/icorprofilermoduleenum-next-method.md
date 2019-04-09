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
ms.openlocfilehash: 57d8279ba9733e6a381d445d50df56b415353a16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077153"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="8d9d3-102">ICorProfilerModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d9d3-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="8d9d3-103">Belirtilen bitişik modül sayısı dizideki geçerli konum Numaralandırıcının başlayarak modüllerinin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d9d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d9d3-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d9d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d9d3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8d9d3-106">[in] Alınacak modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="8d9d3-107">[out] Bir dizi `ModuleID` değerler, her biri alınan bir modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8d9d3-108">[out] Gerçekte döndürülen öğe sayısına bir işaretçi `ids` dizisi.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d9d3-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d9d3-109">Return Value</span></span>  
 <span data-ttu-id="8d9d3-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8d9d3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d9d3-111">HRESULT</span></span>|<span data-ttu-id="8d9d3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d9d3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d9d3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d9d3-113">S_OK</span></span>|`celt` <span data-ttu-id="8d9d3-114">öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-114">elements were returned.</span></span>|  
|<span data-ttu-id="8d9d3-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8d9d3-115">S_FALSE</span></span>|<span data-ttu-id="8d9d3-116">Az `celt` öğeleri döndürüldü, numaralandırma tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d9d3-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d9d3-117">Requirements</span></span>  
 <span data-ttu-id="8d9d3-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d9d3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d9d3-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d9d3-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d9d3-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d9d3-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8d9d3-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8d9d3-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d9d3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-122">See also</span></span>

- [<span data-ttu-id="8d9d3-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d9d3-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="8d9d3-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8d9d3-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
