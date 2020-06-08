---
title: ICorProfilerInfo3::GetThreadStaticAddress2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: a27e7ca156ca138078215a65486ac4b965c6a93d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496340"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="07496-102">ICorProfilerInfo3::GetThreadStaticAddress2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07496-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="07496-103">Belirtilen iş parçacığının ve uygulama etki alanının kapsamındaki belirtilen thread-static alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="07496-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07496-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07496-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07496-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07496-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="07496-106">'ndaki İstenen iş parçacığı-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07496-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="07496-107">'ndaki İstenen iş parçacığı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="07496-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="07496-108">'ndaki Uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07496-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="07496-109">'ndaki İstenen statik alan için kapsam olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07496-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="07496-110">dışı Belirtilen iş parçacığı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07496-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07496-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07496-111">Remarks</span></span>  
 <span data-ttu-id="07496-112">`GetThreadStaticAddress2`Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="07496-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="07496-113">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="07496-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="07496-114">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="07496-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="07496-115">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="07496-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="07496-116">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetThreadStaticAddress2` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="07496-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="07496-117">[ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) yöntemi `GetThreadStaticAddress2` yöntemine benzer, ancak bir uygulama etki alanı bağımsız değişkenini kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="07496-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07496-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07496-118">Requirements</span></span>  
 <span data-ttu-id="07496-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07496-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07496-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="07496-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07496-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07496-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07496-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07496-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07496-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07496-123">See also</span></span>

- [<span data-ttu-id="07496-124">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07496-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="07496-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07496-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="07496-126">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07496-126">Profiling</span></span>](index.md)
