---
title: ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi
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
ms.openlocfilehash: 876ae07a432bfa36a7d9f43ae6c32ec03d7d3289
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496600"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="cac08-102">ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cac08-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="cac08-103">[FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve bağımsız değişken bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cac08-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="cac08-104">Bu yöntem yalnızca `FunctionEnter3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="cac08-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac08-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cac08-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cac08-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cac08-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cac08-107">'ndaki `FunctionID`Girilen işlevin.</span><span class="sxs-lookup"><span data-stu-id="cac08-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="cac08-108">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="cac08-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="cac08-109">Profil Oluşturucu, `eltInfo` [FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından verilen aynısını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cac08-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="cac08-110">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="cac08-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="cac08-111">Bu tanıtıcı yalnızca `FunctionEnter3WithInfo` profil oluşturucunun yöntemi olarak çağrıldığı geri çağırma sırasında geçerlidir `GetFunctionEnter3Info` .</span><span class="sxs-lookup"><span data-stu-id="cac08-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="cac08-112">[in, out] [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısının bayt cinsinden toplam boyutuna yönelik bir işaretçi (artı tarafından işaret edilen bağımsız değişken aralıkları için ek [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıları `pArgumentInfo` ).</span><span class="sxs-lookup"><span data-stu-id="cac08-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="cac08-113">Belirtilen boyut yeterince yoksa, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut içinde depolanır `pcbArgumentInfo` .</span><span class="sxs-lookup"><span data-stu-id="cac08-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="cac08-114">`GetFunctionEnter3Info`İçin yalnızca beklenen değeri almak üzere çağırmak için `*pcbArgumentInfo` , set `*pcbArgumentInfo` = 0 ve `pArgumentInfo` = null.</span><span class="sxs-lookup"><span data-stu-id="cac08-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="cac08-115">dışı İşlevin bellekteki bağımsız değişkenlerinin konumlarını soldan sağa sırada açıklayan [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cac08-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cac08-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cac08-116">Remarks</span></span>  
 <span data-ttu-id="cac08-117">Profil Oluşturucu incelenen işlevin yapısı için yeterli alan ayırmalıdır `COR_PRF_FUNCTION_ARGUMENT_INFO` ve parametresindeki boyutu belirtmelidir `pcbArgumentInfo` .</span><span class="sxs-lookup"><span data-stu-id="cac08-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac08-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cac08-118">Requirements</span></span>  
 <span data-ttu-id="cac08-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cac08-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac08-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cac08-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cac08-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cac08-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cac08-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cac08-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac08-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cac08-123">See also</span></span>

- [<span data-ttu-id="cac08-124">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="cac08-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="cac08-125">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="cac08-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="cac08-126">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="cac08-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="cac08-127">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cac08-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cac08-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cac08-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cac08-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cac08-129">Profiling</span></span>](index.md)
