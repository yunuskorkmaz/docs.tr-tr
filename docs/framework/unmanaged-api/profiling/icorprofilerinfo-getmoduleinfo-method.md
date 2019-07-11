---
title: ICorProfilerInfo::GetModuleInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ceca2133068d3ed011b9499024d127a3dd9279ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782778"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="fc32a-102">ICorProfilerInfo::GetModuleInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc32a-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="fc32a-103">Bir modül kimliği söz konusu modülün dosya adı ve modülün üst derleme Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc32a-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc32a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc32a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc32a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc32a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="fc32a-106">[in] Bilgileri alınır modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="fc32a-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="fc32a-107">[out] Modülün yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="fc32a-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fc32a-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="fc32a-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fc32a-109">[out] Bir işaretçi döndürülür modülün dosya adının toplam karakter uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="fc32a-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="fc32a-110">[out] Bir çağıran tarafından sağlanan geniş karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="fc32a-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="fc32a-111">Yöntem döndürüldüğünde bu arabellek modülü dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="fc32a-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="fc32a-112">[out] Modülün üst derleme kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc32a-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc32a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc32a-113">Remarks</span></span>  
 <span data-ttu-id="fc32a-114">Dinamik modüller için `szName` parametresi boş bir dize ve 0 (sıfır) taban adresidir.</span><span class="sxs-lookup"><span data-stu-id="fc32a-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="fc32a-115">Ancak `GetModuleInfo` yöntemi çağrıldığında modülün kimliği var. hemen sonra Profil Oluşturucu alıncaya kadar üst derlemesinin kimliği kullanılabilir olmayacak [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fc32a-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="fc32a-116">Zaman `GetModuleInfo` döndürür, doğrulamalısınız `szName` arabellek modülün tam dosya adını içerecek şekilde büyük.</span><span class="sxs-lookup"><span data-stu-id="fc32a-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="fc32a-117">Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="fc32a-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="fc32a-118">Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetModuleInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="fc32a-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="fc32a-119">Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="fc32a-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fc32a-120">Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcchName` ve çağrı `GetModuleInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="fc32a-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc32a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc32a-121">Requirements</span></span>  
 <span data-ttu-id="fc32a-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc32a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc32a-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc32a-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc32a-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc32a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc32a-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc32a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc32a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc32a-126">See also</span></span>

- [<span data-ttu-id="fc32a-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc32a-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="fc32a-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fc32a-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fc32a-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc32a-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="fc32a-130">GetModuleInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc32a-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
