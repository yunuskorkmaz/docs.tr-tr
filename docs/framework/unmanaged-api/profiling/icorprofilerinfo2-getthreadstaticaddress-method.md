---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetThreadStaticAddress yöntemi'
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
ms.openlocfilehash: bab4190f3751967031806dccbea2fdf6add73f6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647061"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="01b70-103">ICorProfilerInfo2::GetThreadStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01b70-103">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>

<span data-ttu-id="01b70-104">Belirtilen iş parçacığının kapsamındaki belirtilen thread-static alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="01b70-104">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b70-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01b70-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01b70-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01b70-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="01b70-107">'ndaki İstenen iş parçacığı-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="01b70-107">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="01b70-108">'ndaki İstenen iş parçacığı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="01b70-108">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="01b70-109">'ndaki İstenen statik alan için kapsam olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="01b70-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="01b70-110">dışı Belirtilen iş parçacığı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01b70-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01b70-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01b70-111">Remarks</span></span>  

 <span data-ttu-id="01b70-112">`GetThreadStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="01b70-112">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="01b70-113">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="01b70-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="01b70-114">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="01b70-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="01b70-115">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu yüzden çöp toplama profil oluşturucular sonra geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="01b70-115">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="01b70-116">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetThreadStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="01b70-116">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b70-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01b70-117">Requirements</span></span>  

 <span data-ttu-id="01b70-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b70-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b70-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01b70-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01b70-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="01b70-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01b70-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b70-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b70-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01b70-122">See also</span></span>

- [<span data-ttu-id="01b70-123">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01b70-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="01b70-124">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01b70-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
