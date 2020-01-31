---
title: ICorProfilerInfo2::GetThreadStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: 2c98f67e20ea36d7fbbb31be2e3761594b674c36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868609"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="4035d-102">ICorProfilerInfo2::GetThreadStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4035d-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="4035d-103">Belirtilen iş parçacığının kapsamındaki belirtilen thread-static alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="4035d-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4035d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4035d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4035d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4035d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4035d-106">'ndaki İstenen iş parçacığı-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4035d-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4035d-107">'ndaki İstenen iş parçacığı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4035d-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="4035d-108">'ndaki İstenen statik alan için kapsam olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4035d-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4035d-109">dışı Belirtilen iş parçacığı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4035d-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4035d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4035d-110">Remarks</span></span>  
 <span data-ttu-id="4035d-111">`GetThreadStaticAddress` yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="4035d-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="4035d-112">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4035d-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="4035d-113">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="4035d-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4035d-114">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu yüzden çöp toplama profil oluşturucular sonra geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4035d-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4035d-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce, statik alanlardan bazıları zaten başlatılmış ve atık toplama nesnelerini kök halinde kullanıma sunabilse de `GetThreadStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4035d-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4035d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4035d-116">Requirements</span></span>  
 <span data-ttu-id="4035d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4035d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4035d-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4035d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4035d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4035d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4035d-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4035d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4035d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4035d-121">See also</span></span>

- [<span data-ttu-id="4035d-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4035d-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4035d-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4035d-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
