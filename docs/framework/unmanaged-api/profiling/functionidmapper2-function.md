---
title: FunctionIDMapper2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92285d6aef41595fd4729aa82a827c3efc09b03f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451899"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="9ad67-102">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="9ad67-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="9ad67-103">Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), veya[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) bu işlev için geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="9ad67-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="9ad67-104">`FunctionIDMapper2` Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ad67-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad67-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ad67-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ad67-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ad67-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="9ad67-107">[in] Eşleştirilmesi için işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9ad67-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="9ad67-108">[in] Çalışma zamanları arasında ayırt etmek için kullanılan veri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9ad67-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="9ad67-109">[out] Profil Oluşturucu ayarlar için bir değer için bir işaretçi `true` almak istiyorsa, `FunctionEnter3`, `FunctionLeave3`, ve `FunctionTailcall3`, veya `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, ve `FunctionTailcall3WithInfo` geri aramalar; Aksi takdirde, bu değerineayarlar`false`.</span><span class="sxs-lookup"><span data-stu-id="9ad67-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ad67-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9ad67-110">Return Value</span></span>  
 <span data-ttu-id="9ad67-111">Profil Oluşturucu yürütme altyapısı bir alternatif işlevi tanımlayıcı olarak kullanan bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ad67-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="9ad67-112">Dönüş değeri null olamaz sürece `false` döndürülür `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="9ad67-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="9ad67-113">Aksi takdirde null dönüş değeri büyük olasılıkla işlemi durdurma dahil, öngörülemeyen sonuçlara üretir.</span><span class="sxs-lookup"><span data-stu-id="9ad67-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ad67-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ad67-114">Remarks</span></span>  
 <span data-ttu-id="9ad67-115">Bu yöntemin genişlettiği [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) istemci veri iletmek için kullanılan ek bir parametre ile işlevi.</span><span class="sxs-lookup"><span data-stu-id="9ad67-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="9ad67-116">İstemci verilerini çalışma zamanları arasında belirsizliğini ortadan kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ad67-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad67-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ad67-117">Requirements</span></span>  
 <span data-ttu-id="9ad67-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad67-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad67-119">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="9ad67-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9ad67-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ad67-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ad67-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad67-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad67-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ad67-122">See Also</span></span>  
 [<span data-ttu-id="9ad67-123">Icorprofilerınfo::setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="9ad67-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="9ad67-124">Icorprofilerınfo3::setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="9ad67-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="9ad67-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="9ad67-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="9ad67-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="9ad67-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="9ad67-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="9ad67-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="9ad67-128">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="9ad67-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="9ad67-129">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="9ad67-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="9ad67-130">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="9ad67-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="9ad67-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9ad67-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
