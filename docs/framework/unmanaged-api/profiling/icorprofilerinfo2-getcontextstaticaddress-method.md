---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02694933aca160e1f2c28554eb6758163ed8efc8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619933"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="49d7c-102">ICorProfilerInfo2::GetContextStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49d7c-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="49d7c-103">Belirtilen bağlamı kapsamında belirtilen bağlam statik alanı için adresi alır.</span><span class="sxs-lookup"><span data-stu-id="49d7c-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49d7c-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49d7c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="49d7c-106">[in] İstenen içerik statik alanı içeren sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="49d7c-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="49d7c-107">[in] İstenen içerik statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="49d7c-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="49d7c-108">[in] İstenen içerik statik alanı kapsamını olan bağlam kimliği.</span><span class="sxs-lookup"><span data-stu-id="49d7c-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="49d7c-109">[out] Belirtilen bağlamı içinde statik alanı adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49d7c-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d7c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49d7c-110">Remarks</span></span>  
 <span data-ttu-id="49d7c-111">`GetContextStaticAddress` Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="49d7c-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="49d7c-112">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanı belirtilen bağlam bir adres değil atandıysa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="49d7c-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="49d7c-113">Adresleri nesnelerin çöp koleksiyonu yığınında olabilir.</span><span class="sxs-lookup"><span data-stu-id="49d7c-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="49d7c-114">Çöp toplamanın ardından, profil oluşturucular geçerli olduğunu varsayın değil için bu adresleri çöp toplamanın ardından geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="49d7c-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="49d7c-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetContextStaticAddress` bazı statik alanlar zaten başlatılmış olabilir ancak tüm kendi statik alanları için CORPROF_E_DATAINCOMPLETE döndürür ve çöp toplama nesneleri kök dizini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="49d7c-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d7c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49d7c-116">Requirements</span></span>  
 <span data-ttu-id="49d7c-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d7c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d7c-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49d7c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49d7c-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49d7c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49d7c-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d7c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d7c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49d7c-121">See also</span></span>

- [<span data-ttu-id="49d7c-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49d7c-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="49d7c-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49d7c-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
