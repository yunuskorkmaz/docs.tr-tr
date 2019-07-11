---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc7b6d1a27faf7bde46305f9c98d98351e6261b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782268"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="9c1b7-102">ICorProfilerInfo2::GetRVAStaticAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="9c1b7-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="9c1b7-103">Belirtilen göreli sanal adres (RVA) statik alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c1b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c1b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c1b7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9c1b7-106">[in] İstenen RVA statik alanı içeren sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="9c1b7-107">[in] İstenen RVA statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="9c1b7-108">[out] Bir işaretçi adresine RVA statik alan.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c1b7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c1b7-109">Remarks</span></span>  
 <span data-ttu-id="9c1b7-110">`GetRVAStaticAddress` Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="9c1b7-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="9c1b7-111">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanı belirtilen bağlam bir adres değil atandıysa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="9c1b7-112">Adresleri nesnelerin çöp koleksiyonu yığınında olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="9c1b7-113">Çöp toplamanın ardından, profil oluşturucular geçerli olduğunu varsayın değil için bu adresleri çöp toplamanın ardından geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="9c1b7-114">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetRVAStaticAddress` bazı statik alanlar zaten başlatıldı ve çöp toplama nesneleri kök dizini değiştirme ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c1b7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c1b7-115">Requirements</span></span>  
 <span data-ttu-id="9c1b7-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c1b7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c1b7-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c1b7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c1b7-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c1b7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c1b7-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c1b7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1b7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c1b7-120">See also</span></span>

- [<span data-ttu-id="9c1b7-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c1b7-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="9c1b7-122">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c1b7-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
