---
title: ICorProfilerInfo::GetAssemblyInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3ac5bd35d12bb4c9d9308dcdff3e1fb8385f6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="e0673-102">ICorProfilerInfo::GetAssemblyInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="e0673-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="e0673-103">Bir derleme kimliği kabul eder ve derlemenin adını ve kendi bildirim modülünden Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0673-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0673-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0673-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e0673-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0673-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="e0673-106">[in] Derleme tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e0673-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e0673-107">[in] Karakter cinsinden uzunluğu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="e0673-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e0673-108">[out] Derlemenin adı toplam karakter uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0673-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0673-109">[out] Çağıran tarafından sağlanan geniş karakter arabellek.</span><span class="sxs-lookup"><span data-stu-id="e0673-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="e0673-110">İşlevi döndüğünde, derleme adı içerir.</span><span class="sxs-lookup"><span data-stu-id="e0673-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="e0673-111">[out] Derleme içeren uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0673-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="e0673-112">[out] Derleme bildirimi modülünün kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0673-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0673-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0673-113">Remarks</span></span>  
 <span data-ttu-id="e0673-114">Bu yöntem döndükten sonra doğrulamanız gerekir `szName` arabellek derlemenin tam adını içerecek kadar büyük.</span><span class="sxs-lookup"><span data-stu-id="e0673-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="e0673-115">Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e0673-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e0673-116">Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetAssemblyInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="e0673-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="e0673-117">Alternatif olarak, ilk çağırabilirsiniz `GetAssemblyInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e0673-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e0673-118">Ardından, döndürülen değer göre arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetAssemblyInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="e0673-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0673-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0673-119">Requirements</span></span>  
 <span data-ttu-id="e0673-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0673-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0673-121">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0673-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0673-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0673-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0673-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0673-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0673-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0673-124">See Also</span></span>  
 [<span data-ttu-id="e0673-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0673-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e0673-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0673-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e0673-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0673-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
