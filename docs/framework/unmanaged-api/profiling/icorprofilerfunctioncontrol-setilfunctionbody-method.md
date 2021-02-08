---
description: ': ICorProfilerFunctionControl:: SetILFunctionBody yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 470eefce5b211adcfd111951be9a004b3bd7d8fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781616"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="21eec-103">ICorProfilerFunctionControl::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21eec-103">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>

<span data-ttu-id="21eec-104">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="21eec-104">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21eec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21eec-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21eec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21eec-106">Parameters</span></span>  

 `cbNewILMethodHeader`  
 <span data-ttu-id="21eec-107">[in] Üstbilgi ve gövdeden sonra gelen yapılar da dahil olmak üzere yeni CIL'in toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="21eec-107">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="21eec-108">[in] Yeni CIL üstbilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21eec-108">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21eec-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21eec-109">Return Value</span></span>  

 <span data-ttu-id="21eec-110">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="21eec-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="21eec-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21eec-111">HRESULT</span></span>|<span data-ttu-id="21eec-112">Description</span><span class="sxs-lookup"><span data-stu-id="21eec-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21eec-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="21eec-113">S_OK</span></span>|<span data-ttu-id="21eec-114">Değişiklik başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="21eec-114">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21eec-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21eec-115">Remarks</span></span>  

 <span data-ttu-id="21eec-116">[ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yönteminden farklı olarak, `SetILFunctionBody` yöntemi yeni CIL gövdesi için gereken belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="21eec-116">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="21eec-117">Bu, profil oluşturucu tarafından sunulan CıL gövdesinin [IMethodMalloc](imethodmalloc-interface.md) arabirimi kullanılarak veya belirli bir Aralık içinde ayrılarak ayrılması gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="21eec-117">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="21eec-118">Herhangi bir yığında ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="21eec-118">It can be allocated on any heap.</span></span> <span data-ttu-id="21eec-119">Profil Oluşturucu, döndürüldüğünden CıL gövdesi için kullanılan belleği serbest bırakabilirsiniz `SetILFunctionBody` .</span><span class="sxs-lookup"><span data-stu-id="21eec-119">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21eec-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21eec-120">Requirements</span></span>  

 <span data-ttu-id="21eec-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21eec-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21eec-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21eec-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21eec-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21eec-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21eec-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21eec-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21eec-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21eec-125">See also</span></span>

- [<span data-ttu-id="21eec-126">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21eec-126">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
