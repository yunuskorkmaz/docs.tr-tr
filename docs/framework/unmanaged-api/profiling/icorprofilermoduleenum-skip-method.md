---
title: ICorProfilerModuleEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34c88b52dcc8d07736b6866d467439654faa9a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681852"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="5b533-102">ICorProfilerModuleEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b533-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="5b533-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="5b533-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b533-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b533-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b533-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b533-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5b533-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="5b533-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b533-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b533-107">Return Value</span></span>  
 <span data-ttu-id="5b533-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="5b533-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5b533-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b533-109">HRESULT</span></span>|<span data-ttu-id="5b533-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b533-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b533-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b533-111">S_OK</span></span>|<span data-ttu-id="5b533-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="5b533-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="5b533-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5b533-113">S_FALSE</span></span>|<span data-ttu-id="5b533-114">Az `celt` öğeler atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b533-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b533-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b533-115">Remarks</span></span>  
 <span data-ttu-id="5b533-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumudur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="5b533-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b533-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b533-117">Requirements</span></span>  
 <span data-ttu-id="5b533-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b533-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b533-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b533-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b533-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b533-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b533-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b533-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b533-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b533-122">See also</span></span>
- [<span data-ttu-id="5b533-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b533-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="5b533-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b533-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
