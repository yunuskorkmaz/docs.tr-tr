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
ms.openlocfilehash: 2d3b01deedd5cd7225c9e54b59ed82a708bad937
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513193"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="747ce-102">ICorProfilerFunctionControl::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="747ce-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="747ce-103">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="747ce-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="747ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="747ce-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="747ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="747ce-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="747ce-106">[in] Üstbilgi ve gövdeden sonra gelen yapılar da dahil olmak üzere yeni CIL'in toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="747ce-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="747ce-107">[in] Yeni CIL üstbilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="747ce-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="747ce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="747ce-108">Return Value</span></span>  
 <span data-ttu-id="747ce-109">Bu yöntem aşağıdaki özel HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="747ce-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="747ce-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="747ce-110">HRESULT</span></span>|<span data-ttu-id="747ce-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="747ce-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="747ce-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="747ce-112">S_OK</span></span>|<span data-ttu-id="747ce-113">Değişiklik başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="747ce-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="747ce-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="747ce-114">Remarks</span></span>  
 <span data-ttu-id="747ce-115">Farklı [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi `SetILFunctionBody` yöntemi yeni CIL gövdesi için gerekli olan belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="747ce-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="747ce-116">Bu profil oluşturucu tarafından sağlanan CIL gövdesinin kullanarak ayrılacak yok anlamına gelir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirim veya belirli bir aralık içinde ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="747ce-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="747ce-117">Herhangi bir yığında ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="747ce-117">It can be allocated on any heap.</span></span> <span data-ttu-id="747ce-118">Profil Oluşturucu sonra CIL gövdesi için kullanılan belleği boşaltabilir `SetILFunctionBody` döndürür.</span><span class="sxs-lookup"><span data-stu-id="747ce-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="747ce-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="747ce-119">Requirements</span></span>  
 <span data-ttu-id="747ce-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="747ce-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="747ce-121">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="747ce-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="747ce-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="747ce-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="747ce-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="747ce-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747ce-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="747ce-124">See also</span></span>
- [<span data-ttu-id="747ce-125">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="747ce-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
