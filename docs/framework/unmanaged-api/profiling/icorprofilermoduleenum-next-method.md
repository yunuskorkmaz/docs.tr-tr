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
ms.openlocfilehash: 974879b854f7a4c18aa4625ea88abb4953123f3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456156"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="523e6-102">ICorProfilerModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="523e6-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="523e6-103">Bitişik modülleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak modüllerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="523e6-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="523e6-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="523e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="523e6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="523e6-106">[in] Alınacak modülleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="523e6-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="523e6-107">[out] Bir dizi `ModuleID` değerleri, her biri alınan bir modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="523e6-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="523e6-108">[out] Gerçekte döndürülen öğe sayısı için bir işaretçi `ids` dizi.</span><span class="sxs-lookup"><span data-stu-id="523e6-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="523e6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="523e6-109">Return Value</span></span>  
 <span data-ttu-id="523e6-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="523e6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="523e6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="523e6-111">HRESULT</span></span>|<span data-ttu-id="523e6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="523e6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="523e6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="523e6-113">S_OK</span></span>|<span data-ttu-id="523e6-114">`celt` öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="523e6-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="523e6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="523e6-115">S_FALSE</span></span>|<span data-ttu-id="523e6-116">Daha az `celt` öğeleri döndürülen numaralandırması tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="523e6-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="523e6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="523e6-117">Requirements</span></span>  
 <span data-ttu-id="523e6-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="523e6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523e6-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="523e6-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="523e6-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="523e6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="523e6-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523e6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523e6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="523e6-122">See Also</span></span>  
 [<span data-ttu-id="523e6-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="523e6-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="523e6-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="523e6-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
