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
ms.openlocfilehash: 1e08d246136b33ffaaea91367d428e0bf2db99c1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864134"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="0cb51-102">ICorProfilerInfo::GetAssemblyInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="0cb51-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="0cb51-103">Bir derleme KIMLIĞI kabul eder ve derlemenin adını ve bildirim modülünün KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cb51-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cb51-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0cb51-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cb51-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="0cb51-106">'ndaki Derlemenin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="0cb51-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0cb51-107">'ndaki `szName`karakter cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0cb51-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0cb51-108">dışı Derlemenin adının toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cb51-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0cb51-109">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="0cb51-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="0cb51-110">İşlev döndüğünde, derlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="0cb51-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="0cb51-111">dışı Derlemeyi içeren uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cb51-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0cb51-112">dışı Derlemenin bildirim modülünün KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cb51-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cb51-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cb51-113">Remarks</span></span>  
 <span data-ttu-id="0cb51-114">Bu yöntem çağrıldıktan sonra, `szName` arabelleğinin derlemenin tam adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0cb51-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="0cb51-115">Bunu yapmak için `pcchName` işaret eden değeri `cchName` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="0cb51-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="0cb51-116">`pcchName`, `cchName`daha büyük bir değere işaret ediyorsa, daha büyük bir `szName` arabelleği ayırın, yeni, daha büyük boyuttaki `cchName` güncelleştirin ve `GetAssemblyInfo` çağırın.</span><span class="sxs-lookup"><span data-stu-id="0cb51-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="0cb51-117">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetAssemblyInfo` sıfır uzunluklu `szName` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb51-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0cb51-118">Daha sonra, `pcchName` döndürülen değere göre arabellek boyutunu ayarlayabilir ve `GetAssemblyInfo` tekrar çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb51-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb51-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cb51-119">Requirements</span></span>  
 <span data-ttu-id="0cb51-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb51-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb51-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0cb51-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cb51-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0cb51-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cb51-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb51-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb51-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cb51-124">See also</span></span>

- [<span data-ttu-id="0cb51-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cb51-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0cb51-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0cb51-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0cb51-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cb51-127">Profiling</span></span>](index.md)
