---
title: ICorProfilerInfo::GetObjectSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetObjectSize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9425938042485c4330fe3fbc50cdabde6451b427
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="7b3cb-102">ICorProfilerInfo::GetObjectSize Metodu</span><span class="sxs-lookup"><span data-stu-id="7b3cb-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="7b3cb-103">Belirtilen nesnenin boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b3cb-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b3cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b3cb-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="7b3cb-106">[in] Nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="7b3cb-107">[out] Nesnenin boyutu, bayt gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b3cb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b3cb-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b3cb-109">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-109">This method is obsolete.</span></span> <span data-ttu-id="7b3cb-110">Bu COR_E_OVERFLOW nesneler için 4 GB'den büyük 64 bit platformlarda döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="7b3cb-111">Kullanım [Icorprofilerınfo4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="7b3cb-112">Aynı türden farklı nesneler genellikle aynı boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="7b3cb-113">Bununla birlikte, dizi veya dize gibi bazı türleri her nesne için farklı bir boyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="7b3cb-114">Tarafından döndürülen boyutu `GetObjectSize` yöntemi nesnesi atık toplama yığında alındıktan sonra oluşabilecek herhangi bir hizalama doldurmaya içermez.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="7b3cb-115">Kullanırsanız `GetObjectSize` atık toplama yığında nesne başka bir nesnenin ilerletileceği yöntemi gerektiği gibi el ile doldurma hizalama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="7b3cb-116">32 bit Windows COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4-bayt hizalama ve COR_PRF_GC_LARGE_OBJECT_HEAP 8-bayt hizalama kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="7b3cb-117">64 bit Windows'ta hizalama her zaman 8 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b3cb-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b3cb-118">Requirements</span></span>  
 <span data-ttu-id="7b3cb-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b3cb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b3cb-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b3cb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b3cb-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b3cb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b3cb-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b3cb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3cb-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b3cb-123">See Also</span></span>  
 [<span data-ttu-id="7b3cb-124">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b3cb-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
