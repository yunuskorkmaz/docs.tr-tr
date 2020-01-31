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
ms.openlocfilehash: d99e5000cdd0d7252764554025815dbace2289f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868687"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="a59d5-102">ICorProfilerInfo2::GetContextStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a59d5-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="a59d5-103">Belirtilen bağlamın kapsamındaki belirtilen context-static alanı için adresi alır.</span><span class="sxs-lookup"><span data-stu-id="a59d5-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a59d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a59d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a59d5-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a59d5-106">'ndaki İstenen bağlam-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a59d5-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="a59d5-107">'ndaki İstenen bağlam-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a59d5-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="a59d5-108">'ndaki İstenen bağlam-statik alanı için kapsam olan bağlamın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a59d5-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="a59d5-109">dışı Belirtilen bağlam içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a59d5-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a59d5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a59d5-110">Remarks</span></span>  
 <span data-ttu-id="a59d5-111">`GetContextStaticAddress` yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="a59d5-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="a59d5-112">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a59d5-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="a59d5-113">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="a59d5-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="a59d5-114">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a59d5-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="a59d5-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce, statik alanlardan bazıları zaten başlatılmış ve atık toplama nesnelerini kök halinde kullanıma sunabilse de `GetContextStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a59d5-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59d5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a59d5-116">Requirements</span></span>  
 <span data-ttu-id="a59d5-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a59d5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59d5-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a59d5-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a59d5-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a59d5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a59d5-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59d5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a59d5-121">See also</span></span>

- [<span data-ttu-id="a59d5-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a59d5-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a59d5-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a59d5-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
