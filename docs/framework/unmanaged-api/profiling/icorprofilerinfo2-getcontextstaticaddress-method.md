---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetContextStaticAddress yöntemi'
title: ICorProfilerInfo2::GetContextStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: 7ea8b81c8b1dba4577e070eda68e760cc39f9131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760521"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="de58c-103">ICorProfilerInfo2::GetContextStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de58c-103">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>

<span data-ttu-id="de58c-104">Belirtilen bağlamın kapsamındaki belirtilen context-static alanı için adresi alır.</span><span class="sxs-lookup"><span data-stu-id="de58c-104">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de58c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de58c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de58c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de58c-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="de58c-107">'ndaki İstenen bağlam-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="de58c-107">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="de58c-108">'ndaki İstenen bağlam-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="de58c-108">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="de58c-109">'ndaki İstenen bağlam-statik alanı için kapsam olan bağlamın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="de58c-109">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="de58c-110">dışı Belirtilen bağlam içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="de58c-110">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de58c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de58c-111">Remarks</span></span>  

 <span data-ttu-id="de58c-112">`GetContextStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="de58c-112">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="de58c-113">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="de58c-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="de58c-114">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="de58c-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="de58c-115">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="de58c-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="de58c-116">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetContextStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="de58c-116">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de58c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de58c-117">Requirements</span></span>  

 <span data-ttu-id="de58c-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de58c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de58c-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="de58c-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de58c-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="de58c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de58c-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de58c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de58c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de58c-122">See also</span></span>

- [<span data-ttu-id="de58c-123">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de58c-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="de58c-124">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de58c-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
