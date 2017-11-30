---
title: ICorProfilerInfo::GetModuleInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 23dc0208b4537530f18c2c282fbe8c3495ba301f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="37c5b-102">ICorProfilerInfo::GetModuleInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="37c5b-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="37c5b-103">Modül kimliği modülün dosya adı ve modülün üst derleme Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="37c5b-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37c5b-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37c5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37c5b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="37c5b-106">[in] Bilgiler alınır modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="37c5b-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="37c5b-107">[out] Modül yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="37c5b-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="37c5b-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabellek.</span><span class="sxs-lookup"><span data-stu-id="37c5b-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="37c5b-109">[out] Toplam karakter uzunluğu döndürülen modülün dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37c5b-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="37c5b-110">[out] Çağıran tarafından sağlanan geniş karakter arabellek.</span><span class="sxs-lookup"><span data-stu-id="37c5b-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="37c5b-111">Yöntem döndüğünde, bu arabellek modülü dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="37c5b-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="37c5b-112">[out] Modülün üst derleme kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37c5b-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37c5b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37c5b-113">Remarks</span></span>  
 <span data-ttu-id="37c5b-114">Dinamik modülleri için `szName` parametresi boş bir dize ve taban adresi 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="37c5b-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="37c5b-115">Ancak `GetModuleInfo` modülün kimliği var hemen yöntemi'nin çağrılabilir, profil oluşturucu alıncaya kadar üst derleme Kimliğini kullanılamaz [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="37c5b-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="37c5b-116">Zaman `GetModuleInfo` döndürür, doğrulamalısınız `szName` arabellek modülü tam dosya adını içerecek kadar büyük.</span><span class="sxs-lookup"><span data-stu-id="37c5b-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="37c5b-117">Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="37c5b-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="37c5b-118">Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetModuleInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="37c5b-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="37c5b-119">Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="37c5b-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="37c5b-120">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetModuleInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="37c5b-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c5b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37c5b-121">Requirements</span></span>  
 <span data-ttu-id="37c5b-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37c5b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c5b-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37c5b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="37c5b-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37c5b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37c5b-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c5b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c5b-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37c5b-126">See Also</span></span>  
 [<span data-ttu-id="37c5b-127">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="37c5b-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="37c5b-128">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37c5b-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="37c5b-129">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="37c5b-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [<span data-ttu-id="37c5b-130">Getmoduleınfo2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="37c5b-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
