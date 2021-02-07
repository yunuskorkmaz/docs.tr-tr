---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetRVAStaticAddress yöntemi'
title: ICorProfilerInfo2::GetRVAStaticAddress Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: e72a136ca0d8462d19c57da021e9429528555dac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716412"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="65f6f-103">ICorProfilerInfo2::GetRVAStaticAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="65f6f-103">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>

<span data-ttu-id="65f6f-104">Belirtilen göreli sanal adres (RVA) statik alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="65f6f-104">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f6f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65f6f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65f6f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65f6f-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="65f6f-107">'ndaki İstenen RVA-statik alanını içeren sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="65f6f-107">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="65f6f-108">'ndaki İstenen RVA-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="65f6f-108">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="65f6f-109">dışı RVA-statik alanının adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65f6f-109">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65f6f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65f6f-110">Remarks</span></span>  

 <span data-ttu-id="65f6f-111">`GetRVAStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="65f6f-111">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="65f6f-112">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="65f6f-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="65f6f-113">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="65f6f-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="65f6f-114">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="65f6f-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="65f6f-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetRVAStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış olabilir ve atık toplama nesnelerini kök olabilir.</span><span class="sxs-lookup"><span data-stu-id="65f6f-115">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65f6f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65f6f-116">Requirements</span></span>  

 <span data-ttu-id="65f6f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f6f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f6f-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="65f6f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65f6f-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65f6f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65f6f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f6f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f6f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f6f-121">See also</span></span>

- [<span data-ttu-id="65f6f-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f6f-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="65f6f-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f6f-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
