---
title: ICorProfilerFunctionEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30e0dbb6b22c7278c0bc207ae60214a582d35e9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454935"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="873ff-102">ICorProfilerFunctionEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="873ff-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="873ff-103">Bitişik işlevleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak işlevlerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="873ff-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="873ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="873ff-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="873ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="873ff-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="873ff-106">[in] Alınacak işlevleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="873ff-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="873ff-107">[out] Bir dizi `COR_PRF_FUNCTION` değerleri, her biri alınan bir işlevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="873ff-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="873ff-108">[out] Gerçekte döndürülen işlev sayısı için bir işaretçi `ids` dizi.</span><span class="sxs-lookup"><span data-stu-id="873ff-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="873ff-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="873ff-109">Return Value</span></span>  
 <span data-ttu-id="873ff-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="873ff-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="873ff-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="873ff-111">HRESULT</span></span>|<span data-ttu-id="873ff-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="873ff-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="873ff-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="873ff-113">S_OK</span></span>|<span data-ttu-id="873ff-114">`celt` öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="873ff-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="873ff-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="873ff-115">S_FALSE</span></span>|<span data-ttu-id="873ff-116">Daha az `celt` öğeleri döndürülen numaralandırması tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="873ff-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="873ff-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="873ff-117">Requirements</span></span>  
 <span data-ttu-id="873ff-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="873ff-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="873ff-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="873ff-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="873ff-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="873ff-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="873ff-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="873ff-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873ff-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="873ff-122">See Also</span></span>  
 [<span data-ttu-id="873ff-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="873ff-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="873ff-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="873ff-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
