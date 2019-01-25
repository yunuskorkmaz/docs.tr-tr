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
ms.openlocfilehash: ba1f357c0d68b5a8b5104569a95433504cc84ee6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675361"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="4ddea-102">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ddea-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="4ddea-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="4ddea-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ddea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ddea-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ddea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ddea-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4ddea-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="4ddea-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ddea-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4ddea-107">Return Value</span></span>  
 <span data-ttu-id="4ddea-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="4ddea-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4ddea-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ddea-109">HRESULT</span></span>|<span data-ttu-id="4ddea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ddea-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ddea-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ddea-111">S_OK</span></span>|<span data-ttu-id="4ddea-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="4ddea-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="4ddea-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4ddea-113">S_FALSE</span></span>|<span data-ttu-id="4ddea-114">Az `celt` öğeler atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ddea-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ddea-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ddea-115">Remarks</span></span>  
 <span data-ttu-id="4ddea-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumudur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="4ddea-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ddea-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ddea-117">Requirements</span></span>  
 <span data-ttu-id="4ddea-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ddea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ddea-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ddea-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ddea-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ddea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ddea-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ddea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddea-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ddea-122">See also</span></span>
- [<span data-ttu-id="4ddea-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ddea-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="4ddea-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4ddea-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
