---
title: ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 3dc5f04504cca632892c16d31c92a33935b356e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497344"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="015f8-102">ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="015f8-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="015f8-103">Belirtilen uygulama etki alanının kapsamındaki belirtilen uygulama etki alanı-statik alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="015f8-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015f8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="015f8-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="015f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="015f8-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="015f8-106">'ndaki İstenen uygulama etki alanı-statik alanını içeren sınıfın sınıf KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="015f8-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="015f8-107">'ndaki İstenen uygulama etki alanı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="015f8-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="015f8-108">'ndaki İstenen statik alan için kapsam olan uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="015f8-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="015f8-109">dışı Belirtilen uygulama etki alanı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="015f8-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="015f8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="015f8-110">Remarks</span></span>  
 <span data-ttu-id="015f8-111">`GetAppDomainStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="015f8-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="015f8-112">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="015f8-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="015f8-113">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="015f8-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="015f8-114">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="015f8-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="015f8-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetAppDomainStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="015f8-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="015f8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="015f8-116">Requirements</span></span>  
 <span data-ttu-id="015f8-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="015f8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="015f8-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="015f8-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="015f8-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="015f8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="015f8-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="015f8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015f8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="015f8-121">See also</span></span>

- [<span data-ttu-id="015f8-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="015f8-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="015f8-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="015f8-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
