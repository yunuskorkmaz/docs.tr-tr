---
title: ICorProfilerInfo2::GetBoxClassLayout Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetBoxClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ef6df997a4ba4369b87789e47ac7ead2206162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="24139-102">ICorProfilerInfo2::GetBoxClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="24139-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="24139-103">Bu kutu içinde belirtilen değer türü bulunduğu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="24139-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24139-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24139-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24139-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24139-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="24139-106">[in] Kutulu değer türü açıklanır sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="24139-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="24139-107">[out] Değer türü sarmalanmış nesne kimliği işaretçisi göre uzaklığı bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="24139-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24139-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24139-108">Remarks</span></span>  
 <span data-ttu-id="24139-109">`pBufferOffset` Değer, değer türü kutusu içinde konumdur.</span><span class="sxs-lookup"><span data-stu-id="24139-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="24139-110">Sonra `pBufferOffset` uygulanan bir Kutulu nesnesine değer türünün sınıf düzeni nesnenin değeri yorumlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24139-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24139-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24139-111">Requirements</span></span>  
 <span data-ttu-id="24139-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24139-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24139-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24139-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24139-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24139-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24139-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24139-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24139-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24139-116">See Also</span></span>  
 [<span data-ttu-id="24139-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24139-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="24139-118">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24139-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
