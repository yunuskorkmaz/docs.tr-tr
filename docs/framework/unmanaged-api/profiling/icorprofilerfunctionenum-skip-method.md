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
ms.openlocfilehash: f0e334c75afee60591db2b4e1f45cf0ec753ee2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992062"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="92eff-102">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92eff-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="92eff-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="92eff-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92eff-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92eff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92eff-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="92eff-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="92eff-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92eff-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92eff-107">Return Value</span></span>  
 <span data-ttu-id="92eff-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="92eff-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="92eff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92eff-109">HRESULT</span></span>|<span data-ttu-id="92eff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92eff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92eff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="92eff-111">S_OK</span></span>|<span data-ttu-id="92eff-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="92eff-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="92eff-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="92eff-113">S_FALSE</span></span>|<span data-ttu-id="92eff-114">Az `celt` öğeler atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="92eff-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92eff-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92eff-115">Remarks</span></span>  
 <span data-ttu-id="92eff-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumudur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="92eff-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92eff-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92eff-117">Requirements</span></span>  
 <span data-ttu-id="92eff-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92eff-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92eff-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92eff-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92eff-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92eff-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92eff-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92eff-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92eff-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92eff-122">See also</span></span>

- [<span data-ttu-id="92eff-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92eff-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="92eff-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92eff-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
