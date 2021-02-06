---
description: ': ICorProfilerInfo:: GetAssemblyInfo yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 64e94031e0e4fc5f768e94b83e4e97c3a9a7cb61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647875"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="258f1-103">ICorProfilerInfo::GetAssemblyInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="258f1-103">ICorProfilerInfo::GetAssemblyInfo Method</span></span>

<span data-ttu-id="258f1-104">Bir derleme KIMLIĞI kabul eder ve derlemenin adını ve bildirim modülünün KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="258f1-104">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="258f1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="258f1-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="258f1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="258f1-106">Parameters</span></span>  

 `assemblyId`  
 <span data-ttu-id="258f1-107">'ndaki Derlemenin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="258f1-107">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="258f1-108">'ndaki Karakter cinsinden uzunluğu `szName` .</span><span class="sxs-lookup"><span data-stu-id="258f1-108">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="258f1-109">dışı Derlemenin adının toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="258f1-109">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="258f1-110">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="258f1-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="258f1-111">İşlev döndüğünde, derlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="258f1-111">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="258f1-112">dışı Derlemeyi içeren uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="258f1-112">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="258f1-113">dışı Derlemenin bildirim modülünün KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="258f1-113">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="258f1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="258f1-114">Remarks</span></span>  

 <span data-ttu-id="258f1-115">Bu yöntem çağrıldıktan sonra, `szName` arabelleğin tam adı içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="258f1-115">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="258f1-116">Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="258f1-116">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="258f1-117">Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetAssemblyInfo` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="258f1-117">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="258f1-118">Alternatif olarak, `GetAssemblyInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="258f1-118">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="258f1-119">Daha sonra, içinde döndürülen değere göre arabellek boyutunu ayarlayabilir `pcchName` ve `GetAssemblyInfo` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="258f1-119">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="258f1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="258f1-120">Requirements</span></span>  

 <span data-ttu-id="258f1-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="258f1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="258f1-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="258f1-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="258f1-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="258f1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="258f1-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="258f1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="258f1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="258f1-125">See also</span></span>

- [<span data-ttu-id="258f1-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="258f1-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="258f1-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="258f1-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="258f1-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="258f1-128">Profiling</span></span>](index.md)
