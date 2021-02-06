---
description: ': ICorProfilerFunctionEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6d176c51788135952127008f2f43545ead1e2369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657066"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="c40a1-103">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c40a1-103">ICorProfilerFunctionEnum::Skip Method</span></span>

<span data-ttu-id="c40a1-104">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="c40a1-104">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c40a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c40a1-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c40a1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c40a1-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="c40a1-107">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="c40a1-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c40a1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c40a1-108">Return Value</span></span>  

 <span data-ttu-id="c40a1-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c40a1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c40a1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c40a1-110">HRESULT</span></span>|<span data-ttu-id="c40a1-111">Description</span><span class="sxs-lookup"><span data-stu-id="c40a1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c40a1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c40a1-112">S_OK</span></span>|<span data-ttu-id="c40a1-113">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="c40a1-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="c40a1-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c40a1-114">S_FALSE</span></span>|<span data-ttu-id="c40a1-115">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="c40a1-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c40a1-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c40a1-116">Remarks</span></span>  

 <span data-ttu-id="c40a1-117">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="c40a1-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c40a1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c40a1-118">Requirements</span></span>  

 <span data-ttu-id="c40a1-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c40a1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c40a1-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c40a1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c40a1-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c40a1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c40a1-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c40a1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c40a1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c40a1-123">See also</span></span>

- [<span data-ttu-id="c40a1-124">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c40a1-124">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="c40a1-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c40a1-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
