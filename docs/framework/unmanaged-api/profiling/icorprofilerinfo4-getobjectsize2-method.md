---
title: ICorProfilerInfo4::GetObjectSize2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetObjectSize2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4898157e6525d3b9da4cfade9862b88252df7b14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="b08d4-102">ICorProfilerInfo4::GetObjectSize2 Metodu</span><span class="sxs-lookup"><span data-stu-id="b08d4-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="b08d4-103">Belirtilen nesnenin boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b08d4-103">Returns the size of a specified object.</span></span> <span data-ttu-id="b08d4-104">Değiştirir [Icorprofilerınfo::getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) ne ifade edilebilir daha büyük olan nesneler boyutlarını raporlama tarafından yöntemi bir `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="b08d4-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b08d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b08d4-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b08d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b08d4-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b08d4-107">[in] Nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="b08d4-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="b08d4-108">[out] Nesnenin boyutu, bayt gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b08d4-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b08d4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b08d4-109">Remarks</span></span>  
 <span data-ttu-id="b08d4-110">Aynı türden farklı nesneler genellikle aynı boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="b08d4-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="b08d4-111">Bununla birlikte, dizi veya dize gibi bazı türleri her nesne için farklı bir boyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="b08d4-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b08d4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b08d4-112">Requirements</span></span>  
 <span data-ttu-id="b08d4-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b08d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b08d4-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b08d4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b08d4-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b08d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b08d4-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b08d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08d4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b08d4-117">See Also</span></span>  
 [<span data-ttu-id="b08d4-118">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b08d4-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
