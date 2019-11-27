---
title: ICorProfilerFunctionControl::SetILFunctionBody Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: f6e2cfe47bdd212e39549544b06bf5b11033a956
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429889"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="48620-102">ICorProfilerFunctionControl::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48620-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="48620-103">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="48620-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48620-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48620-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48620-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48620-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="48620-106">[in] Üstbilgi ve gövdeden sonra gelen yapılar da dahil olmak üzere yeni CIL'in toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="48620-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="48620-107">[in] Yeni CIL üstbilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="48620-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48620-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48620-108">Return Value</span></span>  
 <span data-ttu-id="48620-109">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="48620-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="48620-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48620-110">HRESULT</span></span>|<span data-ttu-id="48620-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48620-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48620-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="48620-112">S_OK</span></span>|<span data-ttu-id="48620-113">Değişiklik başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="48620-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48620-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48620-114">Remarks</span></span>  
 <span data-ttu-id="48620-115">[ICorProfilerInfo:: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yönteminden farklı olarak `SetILFunctionBody` yöntemi, yenı CIL gövdesi için gereken belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="48620-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="48620-116">Bu, profil oluşturucu tarafından sunulan CıL gövdesinin [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimi kullanılarak veya belirli bir Aralık içinde ayrılarak ayrılması gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48620-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="48620-117">Herhangi bir yığında ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="48620-117">It can be allocated on any heap.</span></span> <span data-ttu-id="48620-118">Profil Oluşturucu, `SetILFunctionBody` döndüğünde, CıL gövdesi için kullanılan belleği serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48620-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48620-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48620-119">Requirements</span></span>  
 <span data-ttu-id="48620-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48620-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48620-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48620-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48620-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="48620-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48620-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48620-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48620-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48620-124">See also</span></span>

- [<span data-ttu-id="48620-125">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48620-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
