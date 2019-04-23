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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad4ebe4e1255ce13974063eef3d0a4feeb5dd92b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083066"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="1895f-102">ICorProfilerInfo::GetAssemblyInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="1895f-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="1895f-103">Bir derleme kimliği kabul eder ve derlemenin adı ve bildirim, modül kimliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="1895f-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1895f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1895f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1895f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1895f-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="1895f-106">[in] Bütünleştirilmiş kod tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1895f-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1895f-107">[in] Karakter cinsinden uzunluğu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="1895f-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1895f-108">[out] Derleme adının toplam karakter uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1895f-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1895f-109">[out] Bir çağıran tarafından sağlanan geniş karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="1895f-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="1895f-110">İşlevi döndüğünde, derlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="1895f-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="1895f-111">[out] Derlemeyi içeren uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1895f-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="1895f-112">[out] Derlemenin bildirimi modül kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1895f-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1895f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1895f-113">Remarks</span></span>  
 <span data-ttu-id="1895f-114">Bu yöntemin dönüşünün ardından doğrulamanız gerekir `szName` arabellek bütünleştirilmiş kodun tam adını içerecek şekilde büyük.</span><span class="sxs-lookup"><span data-stu-id="1895f-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="1895f-115">Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1895f-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="1895f-116">Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetAssemblyInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="1895f-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="1895f-117">Alternatif olarak, ilk çağırabilirsiniz `GetAssemblyInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="1895f-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1895f-118">Ardından döndürülen değere göre arabellek boyutu ayarlayabileceğiniz `pcchName` ve çağrı `GetAssemblyInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="1895f-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1895f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1895f-119">Requirements</span></span>  
 <span data-ttu-id="1895f-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1895f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1895f-121">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1895f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1895f-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1895f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1895f-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1895f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1895f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1895f-124">See also</span></span>

- [<span data-ttu-id="1895f-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1895f-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1895f-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1895f-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1895f-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1895f-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
