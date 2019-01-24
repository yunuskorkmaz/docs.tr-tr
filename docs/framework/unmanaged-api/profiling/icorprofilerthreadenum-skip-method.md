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
ms.openlocfilehash: f94ce2f5e19636f581918550ee1f651dc1d2d253
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526580"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="84ecc-102">ICorProfilerThreadEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84ecc-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="84ecc-103">Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="84ecc-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ecc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84ecc-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84ecc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84ecc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="84ecc-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="84ecc-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84ecc-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="84ecc-107">Return Value</span></span>  
 <span data-ttu-id="84ecc-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="84ecc-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="84ecc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84ecc-109">HRESULT</span></span>|<span data-ttu-id="84ecc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84ecc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84ecc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="84ecc-111">S_OK</span></span>|<span data-ttu-id="84ecc-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="84ecc-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="84ecc-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="84ecc-113">S_FALSE</span></span>|<span data-ttu-id="84ecc-114">Az `celt` öğeler atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84ecc-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84ecc-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84ecc-115">Remarks</span></span>  
 <span data-ttu-id="84ecc-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumudur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="84ecc-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84ecc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84ecc-117">Requirements</span></span>  
 <span data-ttu-id="84ecc-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84ecc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84ecc-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84ecc-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84ecc-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84ecc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84ecc-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84ecc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ecc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84ecc-122">See also</span></span>
- [<span data-ttu-id="84ecc-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84ecc-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="84ecc-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="84ecc-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
