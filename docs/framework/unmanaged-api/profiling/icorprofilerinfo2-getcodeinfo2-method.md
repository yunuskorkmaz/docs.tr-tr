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
ms.openlocfilehash: 9295ea8b22f72529f55cbe13f6a79a0aa34d2fa0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868802"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="2dd5b-102">ICorProfilerInfo2::GetCodeInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2dd5b-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="2dd5b-103">Belirtilen `FunctionID`ilişkili yerel kod kapsamlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dd5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dd5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dd5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2dd5b-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="2dd5b-106">'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="2dd5b-107">'ndaki `codeInfos` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="2dd5b-108">dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="2dd5b-109">dışı Arayan tarafından sağlanmış arabellek.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="2dd5b-110">Yöntemi çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` yapıları dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2dd5b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2dd5b-111">Remarks</span></span>  
 <span data-ttu-id="2dd5b-112">Kapsamlar, Microsoft ara dili (MSIL) kaydırmasının artırılması sırasında sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="2dd5b-113">`GetCodeInfo2` çağrıldıktan sonra, `codeInfos` arabelleğinin tüm `COR_PRF_CODE_INFO` yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="2dd5b-114">Bunu yapmak için `cCodeInfos` değerini `cchName` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="2dd5b-115">`COR_PRF_CODE_INFO` yapısına bölünen `cCodeInfos`, `pcCodeInfos`daha küçüktür, daha büyük bir `codeInfos` arabelleği ayırın, yeni, daha büyük boyutlu `cCodeInfos` güncelleştirin ve `GetCodeInfo2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="2dd5b-116">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetCodeInfo2` sıfır uzunluklu `codeInfos` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2dd5b-117">Daha sonra `codeInfos` arabellek boyutunu `pcCodeInfos`döndürülen değere ayarlayabilirsiniz, bir `COR_PRF_CODE_INFO` yapısının boyutuyla çarpılır ve `GetCodeInfo2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dd5b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2dd5b-118">Requirements</span></span>  
 <span data-ttu-id="2dd5b-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dd5b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dd5b-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2dd5b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2dd5b-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2dd5b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dd5b-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dd5b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd5b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd5b-123">See also</span></span>

- [<span data-ttu-id="2dd5b-124">GetCodeInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2dd5b-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="2dd5b-125">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dd5b-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="2dd5b-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2dd5b-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2dd5b-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2dd5b-127">Profiling</span></span>](index.md)
