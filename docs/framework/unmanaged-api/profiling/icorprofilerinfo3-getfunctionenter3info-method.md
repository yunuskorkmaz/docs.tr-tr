---
title: ICorProfilerInfo3::GetFunctionEnter3Info Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a12e747344f4943dafced2402e0f08a08ac6e7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498244"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="6c05b-102">ICorProfilerInfo3::GetFunctionEnter3Info Metodu</span><span class="sxs-lookup"><span data-stu-id="6c05b-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="6c05b-103">Profil Oluşturucu tarafından bildirilen işlev yığın çerçeve ve bağımsız değişken bilgilerini sağlar [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="6c05b-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="6c05b-104">Bu yöntem yalnızca sırasında çağrılabilir `FunctionEnter3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6c05b-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c05b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c05b-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c05b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c05b-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6c05b-107">[in] `FunctionID` İşlevinin giriliyor.</span><span class="sxs-lookup"><span data-stu-id="6c05b-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="6c05b-108">[in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="6c05b-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6c05b-109">Profil Oluşturucu, aynı sağlamalıdır `eltInfo` tarafından verildiğini [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="6c05b-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="6c05b-110">[out] Genel türler belirtilen yığın çerçevesi bilgilerini temsil eden bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="6c05b-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="6c05b-111">Bu işleyici yalnızca sırasında geçerli `FunctionEnter3WithInfo` profil oluşturucu çağrılır, geri çağırma `GetFunctionEnter3Info` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6c05b-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="6c05b-112">[out içinde] Bayt olarak toplam boyutu için bir işaretçi, [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) yapısı (artı ek [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) tarafındanişaretedilenbağımsızdeğişkenaralıklarıiçinyapılar`pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="6c05b-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="6c05b-113">Belirtilen boyutu yeterli değil, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut depolanan `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="6c05b-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="6c05b-114">Çağrılacak `GetFunctionEnter3Info` yalnızca beklenen değer almak için `*pcbArgumentInfo`ayarlayın `*pcbArgumentInfo`= 0 ve `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="6c05b-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="6c05b-115">[out] Bir işaretçi bir [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) işlev bağımsız soldan sağa doğru sırayla bellekte konumlarını tanımlayan yapısı.</span><span class="sxs-lookup"><span data-stu-id="6c05b-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c05b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c05b-116">Remarks</span></span>  
 <span data-ttu-id="6c05b-117">Profil Oluşturucu için yeterli alanı ayırmalısınız `COR_PRF_FUNCTION_ARGUMENT_INFO` denetlenen ve boyutunu belirtmeniz gerekir işlev yapısını `pcbArgumentInfo` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6c05b-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c05b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c05b-118">Requirements</span></span>  
 <span data-ttu-id="6c05b-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c05b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c05b-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c05b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c05b-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c05b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c05b-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c05b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c05b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c05b-123">See also</span></span>
- [<span data-ttu-id="6c05b-124">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="6c05b-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="6c05b-125">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="6c05b-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="6c05b-126">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="6c05b-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6c05b-127">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c05b-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6c05b-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c05b-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6c05b-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c05b-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
