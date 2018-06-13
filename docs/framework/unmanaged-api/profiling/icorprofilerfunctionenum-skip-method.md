---
title: ICorProfilerFunctionEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95301c4a99253261721c7f524b99f79a6207feb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453115"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="e9b08-102">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9b08-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="e9b08-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="e9b08-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9b08-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9b08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9b08-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e9b08-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="e9b08-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9b08-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9b08-107">Return Value</span></span>  
 <span data-ttu-id="e9b08-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e9b08-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e9b08-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9b08-109">HRESULT</span></span>|<span data-ttu-id="e9b08-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9b08-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9b08-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9b08-111">S_OK</span></span>|<span data-ttu-id="e9b08-112">`celt` öğeleri atlandı.</span><span class="sxs-lookup"><span data-stu-id="e9b08-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="e9b08-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e9b08-113">S_FALSE</span></span>|<span data-ttu-id="e9b08-114">Daha az `celt` öğeleri atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9b08-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9b08-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9b08-115">Remarks</span></span>  
 <span data-ttu-id="e9b08-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumdur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="e9b08-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9b08-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9b08-117">Requirements</span></span>  
 <span data-ttu-id="e9b08-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9b08-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9b08-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9b08-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9b08-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9b08-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9b08-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9b08-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b08-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9b08-122">See Also</span></span>  
 [<span data-ttu-id="e9b08-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9b08-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="e9b08-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e9b08-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
