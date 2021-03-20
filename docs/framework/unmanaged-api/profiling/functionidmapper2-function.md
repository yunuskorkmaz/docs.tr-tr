---
description: 'Daha fazla bilgi edinin: Functionıdmapper2 Işlevi'
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
ms.openlocfilehash: 8d1b2de62e75665de7116b28a4aa68246dda7bbd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759540"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="01eff-103">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="01eff-103">FunctionIDMapper2 Function</span></span>

<span data-ttu-id="01eff-104">Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md)veya[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) geri çağırmalar içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="01eff-104">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="01eff-105">`FunctionIDMapper2` Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="01eff-105">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01eff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01eff-106">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01eff-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01eff-107">Parameters</span></span>

<span data-ttu-id="01eff-108">`funcId` 'ndaki Yeniden eşleştirilecek işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="01eff-108">`funcId` [in] The function identifier to be remapped.</span></span>

<span data-ttu-id="01eff-109">`clientData` 'ndaki Çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılan veriler için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01eff-109">`clientData` [in] A pointer to data that is used to disambiguate among runtimes.</span></span>

<span data-ttu-id="01eff-110">`pbHookFunction` dışı Profil oluşturucunun,,, `true` , veya, ve geri çağırmaları almak istiyorsa,, ve,, ve geri çağırmaları için ayarladığı değere yönelik bir işaretçi `FunctionEnter3` `FunctionLeave3` `FunctionTailcall3` `FunctionEnter3WithInfo` `FunctionLeave3WithInfo` `FunctionTailcall3WithInfo` ; Aksi takdirde, bu değeri olarak ayarlar `false` .</span><span class="sxs-lookup"><span data-stu-id="01eff-110">`pbHookFunction` [out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="01eff-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="01eff-111">Return Value</span></span>  

 <span data-ttu-id="01eff-112">Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="01eff-112">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="01eff-113">Dönüş değeri, `false` içinde döndürülmediği takdirde null olamaz `pbHookFunction` .</span><span class="sxs-lookup"><span data-stu-id="01eff-113">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="01eff-114">Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi büyük olasılıkla halele vermez.</span><span class="sxs-lookup"><span data-stu-id="01eff-114">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01eff-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01eff-115">Remarks</span></span>  

 <span data-ttu-id="01eff-116">Bu yöntem, [FunctionIDMapper](functionidmapper-function.md) işlevini, istemci verilerini iletmek için kullanılan ek bir parametre ile genişletir.</span><span class="sxs-lookup"><span data-stu-id="01eff-116">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="01eff-117">İstemci verileri, çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01eff-117">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01eff-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01eff-118">Requirements</span></span>  

 <span data-ttu-id="01eff-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01eff-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01eff-120">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="01eff-120">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="01eff-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="01eff-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01eff-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01eff-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01eff-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01eff-123">See also</span></span>

- [<span data-ttu-id="01eff-124">ICorProfilerInfo:: SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="01eff-124">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="01eff-125">ICorProfilerInfo3:: Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="01eff-125">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="01eff-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="01eff-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="01eff-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="01eff-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="01eff-128">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="01eff-128">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="01eff-129">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="01eff-129">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="01eff-130">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="01eff-130">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="01eff-131">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="01eff-131">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="01eff-132">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="01eff-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
