---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973701"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="e4dba-102">ICorProfilerInfo9:: GetCodeInfo4 yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4dba-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>
  
 <span data-ttu-id="e4dba-103">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4dba-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e4dba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4dba-104">Syntax</span></span>  
  
```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4dba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4dba-105">Parameters</span></span>  
 `pNativeCodeStartAddress`  
 <span data-ttu-id="e4dba-106">'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4dba-106">[in] A pointer to the start of a native function.</span></span>  

 `cCodeInfos`  
 <span data-ttu-id="e4dba-107">'ndaki `codeInfos` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e4dba-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="e4dba-108">dışı Kullanılabilir toplam [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4dba-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="e4dba-109">dışı Arayan tarafından sağlanmış arabellek.</span><span class="sxs-lookup"><span data-stu-id="e4dba-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="e4dba-110">Yöntem çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` bir yapı dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="e4dba-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4dba-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4dba-111">Remarks</span></span>  
 <span data-ttu-id="e4dba-112">Yöntemi, bir yöntemin farklı yerel sürümleri için kod bilgilerini aramak dışında, GetCodeInfo3 ile benzerdir. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) `GetCodeInfo4`</span><span class="sxs-lookup"><span data-stu-id="e4dba-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4dba-113">`GetCodeInfo4`bir çöp toplama tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e4dba-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>
  
 <span data-ttu-id="e4dba-114">Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e4dba-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="e4dba-115">Geri döndüğünde, `codeInfos` arabelleğin tüm COR_PRF_CODE_INFO yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `GetCodeInfo4`</span><span class="sxs-lookup"><span data-stu-id="e4dba-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="e4dba-116">Bunu yapmak için değerini `cCodeInfos` `cchName` parametresinin değeriyle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="e4dba-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e4dba-117">`codeInfos` `cCodeInfos` `GetCodeInfo4` [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) BirCOR_PRF_CODE_INFO`pcCodeInfos`yapısının boyutuna göre ayrılmışsa,dahaküçükbirarabellekayırarak,yeni,dahabüyükboyutlagüncelleştirin`cCodeInfos` ve yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="e4dba-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>  
  
 <span data-ttu-id="e4dba-118">Alternatif olarak, doğru arabellek boyutunu `GetCodeInfo4` elde etmek için ilk olarak `codeInfos` sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4dba-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e4dba-119">Daha sonra `codeInfos` arabellek boyutunu ' de `pcCodeInfos`döndürülen değere ayarlayabilir, bir COR_PRF_CODE_INFO yapısının boyutuyla çarpılır ve yeniden çağırabilirsiniz. [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `GetCodeInfo4`</span><span class="sxs-lookup"><span data-stu-id="e4dba-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>   
  

## <a name="requirements"></a><span data-ttu-id="e4dba-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4dba-120">Requirements</span></span>  
 <span data-ttu-id="e4dba-121">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="e4dba-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="e4dba-122">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e4dba-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4dba-123">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e4dba-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4dba-124">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4dba-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="e4dba-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4dba-125">See also</span></span>
- [<span data-ttu-id="e4dba-126">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4dba-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

