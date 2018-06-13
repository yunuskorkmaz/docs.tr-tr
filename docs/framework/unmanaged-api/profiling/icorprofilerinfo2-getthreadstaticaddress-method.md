---
title: ICorProfilerInfo2::GetThreadStaticAddress Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a38c8323157cee866ac0ecab97532b9b72a932b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454134"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="27b32-102">ICorProfilerInfo2::GetThreadStaticAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="27b32-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="27b32-103">Belirtilen iş parçacığı kapsamında belirtilen statik iş parçacığı alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="27b32-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27b32-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27b32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27b32-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="27b32-106">[in] İstenen iş parçacığı statik alan içeren sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="27b32-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="27b32-107">[in] İstenen iş parçacığı statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="27b32-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="27b32-108">[in] İstenen statik alanın kapsamı iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="27b32-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="27b32-109">[out] Belirtilen iş parçacığı içinde statik alan adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27b32-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27b32-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27b32-110">Remarks</span></span>  
 <span data-ttu-id="27b32-111">`GetThreadStaticAddress` Yöntemi döndürebilir şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="27b32-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="27b32-112">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="27b32-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="27b32-113">Çöp toplama yığınında olabilir nesneleri adresleri.</span><span class="sxs-lookup"><span data-stu-id="27b32-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="27b32-114">Bu adresler çöp toplama sonra geçersiz hale gelebilir bunu atık toplama profil oluşturucular geçerli varsayımında bulunmamalıdır sonra.</span><span class="sxs-lookup"><span data-stu-id="27b32-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="27b32-115">Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetThreadStaticAddress` statik alanları bazıları zaten başlatılmamış olabilir ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür ve atık toplama nesneleri kök dizini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="27b32-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27b32-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27b32-116">Requirements</span></span>  
 <span data-ttu-id="27b32-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27b32-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27b32-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27b32-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27b32-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27b32-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27b32-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27b32-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b32-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27b32-121">See Also</span></span>  
 [<span data-ttu-id="27b32-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27b32-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="27b32-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27b32-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
