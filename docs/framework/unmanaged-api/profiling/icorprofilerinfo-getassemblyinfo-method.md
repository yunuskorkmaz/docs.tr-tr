---
title: ICorProfilerInfo::GetAssemblyInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 41083b2fcd61a9a726e835c3d5710308aa634600
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498654"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="9f01c-102">ICorProfilerInfo::GetAssemblyInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="9f01c-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="9f01c-103">Bir derleme KIMLIĞI kabul eder ve derlemenin adını ve bildirim modülünün KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f01c-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f01c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9f01c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f01c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f01c-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="9f01c-106">'ndaki Derlemenin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9f01c-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9f01c-107">'ndaki Karakter cinsinden uzunluğu `szName` .</span><span class="sxs-lookup"><span data-stu-id="9f01c-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9f01c-108">dışı Derlemenin adının toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f01c-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9f01c-109">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="9f01c-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="9f01c-110">İşlev döndüğünde, derlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="9f01c-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="9f01c-111">dışı Derlemeyi içeren uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f01c-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="9f01c-112">dışı Derlemenin bildirim modülünün KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f01c-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f01c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f01c-113">Remarks</span></span>  
 <span data-ttu-id="9f01c-114">Bu yöntem çağrıldıktan sonra, `szName` arabelleğin tam adı içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f01c-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="9f01c-115">Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="9f01c-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9f01c-116">Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetAssemblyInfo` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="9f01c-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="9f01c-117">Alternatif olarak, `GetAssemblyInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f01c-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9f01c-118">Daha sonra, içinde döndürülen değere göre arabellek boyutunu ayarlayabilir `pcchName` ve `GetAssemblyInfo` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f01c-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f01c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f01c-119">Requirements</span></span>  
 <span data-ttu-id="9f01c-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f01c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f01c-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9f01c-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f01c-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f01c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f01c-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f01c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f01c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f01c-124">See also</span></span>

- [<span data-ttu-id="9f01c-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f01c-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="9f01c-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9f01c-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9f01c-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f01c-127">Profiling</span></span>](index.md)
