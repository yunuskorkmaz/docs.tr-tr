---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetAppDomainStaticAddress yöntemi'
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
ms.openlocfilehash: 4ef8511e75a18f7626fa7a30ea194140de051bb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753243"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="cb0c0-103">ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb0c0-103">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>

<span data-ttu-id="cb0c0-104">Belirtilen uygulama etki alanının kapsamındaki belirtilen uygulama etki alanı-statik alanının adresini alır.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-104">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb0c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb0c0-105">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb0c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb0c0-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="cb0c0-107">'ndaki İstenen uygulama etki alanı-statik alanını içeren sınıfın sınıf KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-107">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="cb0c0-108">'ndaki İstenen uygulama etki alanı-statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-108">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="cb0c0-109">'ndaki İstenen statik alan için kapsam olan uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-109">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="cb0c0-110">dışı Belirtilen uygulama etki alanı içindeki statik alanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-110">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb0c0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb0c0-111">Remarks</span></span>  

 <span data-ttu-id="cb0c0-112">`GetAppDomainStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="cb0c0-112">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="cb0c0-113">Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="cb0c0-114">Çöp toplama yığınında olabilecek nesnelerin adresleri.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="cb0c0-115">Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="cb0c0-116">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetAppDomainStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-116">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb0c0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb0c0-117">Requirements</span></span>  

 <span data-ttu-id="cb0c0-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb0c0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb0c0-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb0c0-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb0c0-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb0c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb0c0-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb0c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0c0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb0c0-122">See also</span></span>

- [<span data-ttu-id="cb0c0-123">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb0c0-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cb0c0-124">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb0c0-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
