---
title: ICorProfilerInfo::GetObjectSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42e86b1eac788b709432d39e320ebea49c696c14
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481717"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="b55dd-102">ICorProfilerInfo::GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b55dd-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="b55dd-103">Belirtilen nesnenin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="b55dd-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b55dd-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b55dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b55dd-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b55dd-106">[in] Nesnenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="b55dd-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="b55dd-107">[out] Nesnenin boyutu, bayt için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b55dd-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b55dd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b55dd-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b55dd-109">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b55dd-109">This method is obsolete.</span></span> <span data-ttu-id="b55dd-110">COR_E_OVERFLOW nesneler için 4 GB değerinden 64-bit platformlarda döndürür.</span><span class="sxs-lookup"><span data-stu-id="b55dd-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="b55dd-111">Kullanım [Icorprofilerınfo4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="b55dd-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="b55dd-112">Aynı türden farklı nesneler genellikle aynı boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="b55dd-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="b55dd-113">Ancak, diziler veya dizeler gibi bazı türleri her nesne için başka bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="b55dd-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="b55dd-114">Tarafından döndürülen boyutla `GetObjectSize` yöntemi nesnenin çöp koleksiyonu yığınında sonra oluşabilecek herhangi bir hizalama doldurmaya içermez.</span><span class="sxs-lookup"><span data-stu-id="b55dd-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="b55dd-115">Kullanırsanız `GetObjectSize` nesne başka bir nesnenin çöp koleksiyonu yığınında ilerlemek için yöntemi el ile gerektiği şekilde doldurma hizalama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b55dd-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="b55dd-116">32 bit Windows üzerinde COR_PRF_GC_GEN_0 COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4 baytlık hizalaması kullanın ve 8 baytlık hizalama COR_PRF_GC_LARGE_OBJECT_HEAP kullanır.</span><span class="sxs-lookup"><span data-stu-id="b55dd-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="b55dd-117">64 bit Windows üzerinde hizalama her zaman 8 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="b55dd-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b55dd-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b55dd-118">Requirements</span></span>  
 <span data-ttu-id="b55dd-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b55dd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b55dd-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b55dd-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b55dd-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b55dd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b55dd-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b55dd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55dd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b55dd-123">See also</span></span>
- [<span data-ttu-id="b55dd-124">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b55dd-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
