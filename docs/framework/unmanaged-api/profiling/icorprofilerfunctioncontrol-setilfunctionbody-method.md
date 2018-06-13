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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b6cab555144c25c5984d74d19d5e81aa1a196d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454974"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="233c9-102">ICorProfilerFunctionControl::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="233c9-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="233c9-103">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="233c9-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="233c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="233c9-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="233c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="233c9-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="233c9-106">[in] Üstbilgi ve gövdeden sonra gelen yapılar da dahil olmak üzere yeni CIL'in toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="233c9-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="233c9-107">[in] Yeni CIL üstbilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="233c9-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="233c9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="233c9-108">Return Value</span></span>  
 <span data-ttu-id="233c9-109">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="233c9-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="233c9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="233c9-110">HRESULT</span></span>|<span data-ttu-id="233c9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="233c9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="233c9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="233c9-112">S_OK</span></span>|<span data-ttu-id="233c9-113">Değişiklik başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="233c9-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="233c9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="233c9-114">Remarks</span></span>  
 <span data-ttu-id="233c9-115">Farklı [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi, `SetILFunctionBody` yöntemi yeni CIL gövdesi için gerekli bellek yönetir.</span><span class="sxs-lookup"><span data-stu-id="233c9-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="233c9-116">Bu profil oluşturucu tarafından sağlanan CIL gövde kullanarak ayrılacak yok anlamına gelir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirim veya belirli bir aralık içinde ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="233c9-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="233c9-117">Herhangi bir yığında ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="233c9-117">It can be allocated on any heap.</span></span> <span data-ttu-id="233c9-118">Profil Oluşturucu sonra onun CIL gövdesi için kullanılan bellek boşaltabilirsiniz `SetILFunctionBody` döndürür.</span><span class="sxs-lookup"><span data-stu-id="233c9-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="233c9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="233c9-119">Requirements</span></span>  
 <span data-ttu-id="233c9-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="233c9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="233c9-121">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="233c9-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="233c9-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="233c9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="233c9-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="233c9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233c9-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="233c9-124">See Also</span></span>  
 [<span data-ttu-id="233c9-125">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="233c9-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
