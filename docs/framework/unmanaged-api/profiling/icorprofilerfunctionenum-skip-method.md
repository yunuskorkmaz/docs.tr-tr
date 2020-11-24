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
ms.openlocfilehash: da578e02db0744b1f64c1d392844aa020721e784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669268"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="d0495-102">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0495-102">ICorProfilerFunctionEnum::Skip Method</span></span>

<span data-ttu-id="d0495-103">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="d0495-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0495-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d0495-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0495-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0495-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d0495-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="d0495-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0495-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0495-107">Return Value</span></span>  

 <span data-ttu-id="d0495-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0495-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d0495-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0495-109">HRESULT</span></span>|<span data-ttu-id="d0495-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0495-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0495-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0495-111">S_OK</span></span>|<span data-ttu-id="d0495-112">`celt` öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="d0495-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="d0495-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d0495-113">S_FALSE</span></span>|<span data-ttu-id="d0495-114">Daha az öğe olmadığını `celt` belirten öğe atlandı.</span><span class="sxs-lookup"><span data-stu-id="d0495-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0495-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0495-115">Remarks</span></span>  

 <span data-ttu-id="d0495-116">Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .</span><span class="sxs-lookup"><span data-stu-id="d0495-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0495-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0495-117">Requirements</span></span>  

 <span data-ttu-id="d0495-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0495-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0495-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d0495-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0495-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0495-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0495-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0495-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0495-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0495-122">See also</span></span>

- [<span data-ttu-id="d0495-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0495-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="d0495-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d0495-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
