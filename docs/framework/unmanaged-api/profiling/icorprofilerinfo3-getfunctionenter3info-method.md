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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177026"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="00662-102">ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00662-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="00662-103">[FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından profiloluşturucuya bildirilen işlevin yığın çerçevesi ve bağımsız değişken bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="00662-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="00662-104">Bu yöntem yalnızca `FunctionEnter3WithInfo` geri arama sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="00662-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00662-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00662-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00662-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00662-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="00662-107">[içinde] Girilen `FunctionID` işlevin.</span><span class="sxs-lookup"><span data-stu-id="00662-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="00662-108">[içinde] Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden opak bir tutamaç.</span><span class="sxs-lookup"><span data-stu-id="00662-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="00662-109">Profil oluşturucu, `eltInfo` [FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından verilenin aynısını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="00662-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="00662-110">[çıkış] Belirli bir yığın çerçevesi hakkında genel bilgileri temsil eden opak bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="00662-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="00662-111">Bu tanıtıcı yalnızca `FunctionEnter3WithInfo` profilleyicinin `GetFunctionEnter3Info` yöntemi çağırdığı geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="00662-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="00662-112">[içinde, dışarı] [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısının toplam boyutuna, baytlarda bir işaretçi (artı işaret `pArgumentInfo`edilen bağımsız değişken aralıkları için ek [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıları).</span><span class="sxs-lookup"><span data-stu-id="00662-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="00662-113">Belirtilen boyut yeterli değilse, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="00662-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="00662-114">`GetFunctionEnter3Info` Beklenen değeri almak için aramak `*pcbArgumentInfo`için `*pcbArgumentInfo`, `pArgumentInfo`set =0 ve =NULL.</span><span class="sxs-lookup"><span data-stu-id="00662-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="00662-115">[çıkış] İşlevin bağımsız değişkenlerinin konumlarını soldan sağa sırayla açıklayan [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) bir yapıya işaretçi.</span><span class="sxs-lookup"><span data-stu-id="00662-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00662-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00662-116">Remarks</span></span>  
 <span data-ttu-id="00662-117">Profil oluşturucu, denetlenmekte `COR_PRF_FUNCTION_ARGUMENT_INFO` olan işlevin yapısı için yeterli alan ayırmalı ve `pcbArgumentInfo` parametredeki boyutu belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="00662-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00662-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00662-118">Requirements</span></span>  
 <span data-ttu-id="00662-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00662-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00662-120">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00662-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00662-121">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00662-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00662-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00662-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00662-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00662-123">See also</span></span>

- [<span data-ttu-id="00662-124">FonksiyonEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00662-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="00662-125">FonksiyonLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00662-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="00662-126">FonksiyonTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00662-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="00662-127">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00662-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="00662-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00662-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="00662-129">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="00662-129">Profiling</span></span>](index.md)
