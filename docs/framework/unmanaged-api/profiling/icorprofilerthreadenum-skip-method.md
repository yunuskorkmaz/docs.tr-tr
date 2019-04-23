---
title: ICorProfilerThreadEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cce96e8c6d046beba9e45c7121bf68444fd51c95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173348"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="49dd5-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49dd5-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="49dd5-103">Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="49dd5-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49dd5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49dd5-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49dd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49dd5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="49dd5-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="49dd5-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49dd5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="49dd5-107">Return Value</span></span>  
 <span data-ttu-id="49dd5-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="49dd5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="49dd5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49dd5-109">HRESULT</span></span>|<span data-ttu-id="49dd5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49dd5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49dd5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="49dd5-111">S_OK</span></span>|<span data-ttu-id="49dd5-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="49dd5-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="49dd5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="49dd5-113">S_FALSE</span></span>|<span data-ttu-id="49dd5-114">Az `celt` öğeler atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="49dd5-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49dd5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49dd5-115">Remarks</span></span>  
 <span data-ttu-id="49dd5-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumudur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="49dd5-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49dd5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49dd5-117">Requirements</span></span>  
 <span data-ttu-id="49dd5-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49dd5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49dd5-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49dd5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49dd5-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49dd5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49dd5-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49dd5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49dd5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49dd5-122">See also</span></span>

- [<span data-ttu-id="49dd5-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49dd5-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="49dd5-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="49dd5-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
