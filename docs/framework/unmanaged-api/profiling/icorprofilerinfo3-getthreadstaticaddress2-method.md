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
ms.openlocfilehash: 5ebd1f2780ab25e01bcb384b38220f414d90292e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868544"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="03017-102">ICorProfilerInfo3::GetThreadStaticAddress2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03017-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="03017-103">Belirtilen iş parçacığının ve uygulama etki alanının kapsamındaki belirtilen thread-static alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="03017-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03017-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03017-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03017-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03017-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="03017-106">'ndaki İstenen iş parçacığı-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="03017-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="03017-107">'ndaki İstenen iş parçacığı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="03017-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="03017-108">'ndaki Uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="03017-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="03017-109">'ndaki İstenen statik alan için kapsam olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="03017-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="03017-110">dışı Belirtilen iş parçacığı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03017-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03017-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03017-111">Remarks</span></span>  
 <span data-ttu-id="03017-112">`GetThreadStaticAddress2` yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="03017-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="03017-113">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="03017-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="03017-114">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="03017-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="03017-115">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="03017-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="03017-116">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce, statik alanlardan bazıları zaten başlatılmış ve atık toplama nesnelerini kök halinde kullanıma sunabilse de `GetThreadStaticAddress2` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="03017-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="03017-117">[ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) yöntemi `GetThreadStaticAddress2` yönteme benzerdir, ancak bir uygulama etki alanı bağımsız değişkenini kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="03017-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03017-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03017-118">Requirements</span></span>  
 <span data-ttu-id="03017-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03017-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03017-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="03017-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03017-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03017-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03017-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03017-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03017-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03017-123">See also</span></span>

- [<span data-ttu-id="03017-124">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03017-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="03017-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="03017-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="03017-126">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="03017-126">Profiling</span></span>](index.md)
