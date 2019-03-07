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
ms.openlocfilehash: e87d466e463cad2d9cd57c341812a0b57e025256
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479434"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="f99f1-102">ICorProfilerFunctionControl::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f99f1-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="f99f1-103">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="f99f1-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f99f1-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f99f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f99f1-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="f99f1-106">[in] Üstbilgi ve gövdeden sonra gelen yapılar da dahil olmak üzere yeni CIL'in toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="f99f1-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="f99f1-107">[in] Yeni CIL üstbilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f99f1-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f99f1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f99f1-108">Return Value</span></span>  
 <span data-ttu-id="f99f1-109">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="f99f1-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="f99f1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f99f1-110">HRESULT</span></span>|<span data-ttu-id="f99f1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f99f1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f99f1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f99f1-112">S_OK</span></span>|<span data-ttu-id="f99f1-113">Değişiklik başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="f99f1-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f99f1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f99f1-114">Remarks</span></span>  
 <span data-ttu-id="f99f1-115">Farklı [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi `SetILFunctionBody` yöntemi yeni CIL gövdesi için gerekli olan belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="f99f1-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="f99f1-116">Bu profil oluşturucu tarafından sağlanan CIL gövdesinin kullanarak ayrılacak yok anlamına gelir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirim veya belirli bir aralık içinde ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f99f1-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="f99f1-117">Herhangi bir yığında ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f99f1-117">It can be allocated on any heap.</span></span> <span data-ttu-id="f99f1-118">Profil Oluşturucu sonra CIL gövdesi için kullanılan belleği boşaltabilir `SetILFunctionBody` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f99f1-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f99f1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f99f1-119">Requirements</span></span>  
 <span data-ttu-id="f99f1-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f99f1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f99f1-121">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f99f1-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f99f1-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f99f1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f99f1-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f99f1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99f1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f99f1-124">See also</span></span>
- [<span data-ttu-id="f99f1-125">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f99f1-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
