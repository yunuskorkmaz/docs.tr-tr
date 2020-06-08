---
title: ICorProfilerInfo2::GetCodeInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502905"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="a0335-102">ICorProfilerInfo2::GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0335-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="a0335-103">Belirtilen yerel kod kapsamlarını alır, bununla ilişkili `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="a0335-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0335-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a0335-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0335-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0335-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="a0335-106">'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a0335-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="a0335-107">'ndaki `codeInfos`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a0335-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="a0335-108">dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a0335-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="a0335-109">dışı Arayan tarafından sağlanmış arabellek.</span><span class="sxs-lookup"><span data-stu-id="a0335-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="a0335-110">Yöntem çağrıldıktan sonra, `COR_PRF_CODE_INFO` her biri yerel kod bloğunu açıklayan bir yapı dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="a0335-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0335-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0335-111">Remarks</span></span>  
 <span data-ttu-id="a0335-112">Kapsamlar, Microsoft ara dili (MSIL) kaydırmasının artırılması sırasında sıralanır.</span><span class="sxs-lookup"><span data-stu-id="a0335-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="a0335-113">`GetCodeInfo2`Geri döndüğünde, `codeInfos` arabelleğin tüm yapıları içerecek kadar büyük olduğunu doğrulamanız gerekir `COR_PRF_CODE_INFO` .</span><span class="sxs-lookup"><span data-stu-id="a0335-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="a0335-114">Bunu yapmak için değerini `cCodeInfos` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="a0335-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a0335-115">`cCodeInfos`Bir yapının boyutuna göre ayrılmışsa `COR_PRF_CODE_INFO` `pcCodeInfos` , daha küçük bir arabellek ayırarak, `codeInfos` `cCodeInfos` Yeni, daha büyük boyutla güncelleştirin ve `GetCodeInfo2` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="a0335-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="a0335-116">Alternatif olarak, `GetCodeInfo2` `codeInfos` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0335-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a0335-117">Daha sonra `codeInfos` arabellek boyutunu ' de döndürülen değere ayarlayabilir `pcCodeInfos` , bir yapının boyutuyla çarpılır `COR_PRF_CODE_INFO` ve `GetCodeInfo2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0335-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0335-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0335-118">Requirements</span></span>  
 <span data-ttu-id="a0335-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0335-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0335-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a0335-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0335-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a0335-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0335-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0335-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0335-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0335-123">See also</span></span>

- [<span data-ttu-id="a0335-124">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0335-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="a0335-125">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0335-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="a0335-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a0335-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a0335-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0335-127">Profiling</span></span>](index.md)
