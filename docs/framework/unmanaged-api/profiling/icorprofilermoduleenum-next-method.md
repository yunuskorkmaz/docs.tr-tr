---
title: "ICorProfilerModuleEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c20b6970c0df30b75bacf76f52c7610bd4a3a5e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="a5aaa-102">ICorProfilerModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5aaa-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="a5aaa-103">Bitişik modülleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak modüllerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5aaa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5aaa-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5aaa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5aaa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a5aaa-106">[in] Alınacak modülleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="a5aaa-107">[out] Bir dizi `ModuleID` değerleri, her biri alınan bir modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a5aaa-108">[out] Gerçekte döndürülen öğe sayısı için bir işaretçi `ids` dizi.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5aaa-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5aaa-109">Return Value</span></span>  
 <span data-ttu-id="a5aaa-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5aaa-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5aaa-111">HRESULT</span></span>|<span data-ttu-id="a5aaa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5aaa-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5aaa-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5aaa-113">S_OK</span></span>|<span data-ttu-id="a5aaa-114">`celt`öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="a5aaa-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a5aaa-115">S_FALSE</span></span>|<span data-ttu-id="a5aaa-116">Daha az `celt` öğeleri döndürülen numaralandırması tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5aaa-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5aaa-117">Requirements</span></span>  
 <span data-ttu-id="a5aaa-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5aaa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5aaa-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5aaa-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5aaa-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5aaa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5aaa-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5aaa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5aaa-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-122">See Also</span></span>  
 [<span data-ttu-id="a5aaa-123">Icorprofilermoduleenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5aaa-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="a5aaa-124">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5aaa-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
