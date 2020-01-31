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
ms.openlocfilehash: 05d8c44655d8670194035c336bd62ae5d53bfec3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862990"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="8d86e-102">ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d86e-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="8d86e-103">Belirtilen uygulama etki alanının kapsamındaki belirtilen uygulama etki alanı-statik alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="8d86e-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d86e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d86e-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d86e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d86e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="8d86e-106">'ndaki İstenen uygulama etki alanı-statik alanını içeren sınıfın sınıf KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8d86e-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="8d86e-107">'ndaki İstenen uygulama etki alanı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8d86e-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="8d86e-108">'ndaki İstenen statik alan için kapsam olan uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8d86e-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="8d86e-109">dışı Belirtilen uygulama etki alanı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d86e-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d86e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d86e-110">Remarks</span></span>  
 <span data-ttu-id="8d86e-111">`GetAppDomainStaticAddress` yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="8d86e-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="8d86e-112">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8d86e-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="8d86e-113">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="8d86e-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="8d86e-114">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d86e-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="8d86e-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce, statik alanlardan bazıları zaten başlatılmış ve atık toplama nesnelerini kök halinde kullanıma sunabilse de `GetAppDomainStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d86e-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d86e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d86e-116">Requirements</span></span>  
 <span data-ttu-id="8d86e-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d86e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d86e-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d86e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d86e-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8d86e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d86e-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d86e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d86e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d86e-121">See also</span></span>

- [<span data-ttu-id="8d86e-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d86e-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8d86e-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d86e-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
