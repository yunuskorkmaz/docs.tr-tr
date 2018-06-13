---
title: ICorProfilerInfo::GetModuleInfo Metodu
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
ms.openlocfilehash: b8ebff6975fdad2427800f5fbb3ef20634c1974d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457015"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="9a9cf-102">ICorProfilerInfo::GetModuleInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="9a9cf-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="9a9cf-103">Modül kimliği modülün dosya adı ve modülün üst derleme Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a9cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a9cf-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9a9cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a9cf-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9a9cf-106">[in] Bilgiler alınır modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="9a9cf-107">[out] Modül yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9a9cf-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabellek.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9a9cf-109">[out] Toplam karakter uzunluğu döndürülen modülün dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a9cf-110">[out] Çağıran tarafından sağlanan geniş karakter arabellek.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="9a9cf-111">Yöntem döndüğünde, bu arabellek modülü dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="9a9cf-112">[out] Modülün üst derleme kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a9cf-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a9cf-113">Remarks</span></span>  
 <span data-ttu-id="9a9cf-114">Dinamik modülleri için `szName` parametresi boş bir dize ve taban adresi 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="9a9cf-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="9a9cf-115">Ancak `GetModuleInfo` modülün kimliği var hemen yöntemi'nin çağrılabilir, profil oluşturucu alıncaya kadar üst derleme Kimliğini kullanılamaz [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="9a9cf-116">Zaman `GetModuleInfo` döndürür, doğrulamalısınız `szName` arabellek modülü tam dosya adını içerecek kadar büyük.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="9a9cf-117">Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9a9cf-118">Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetModuleInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="9a9cf-119">Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9a9cf-120">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetModuleInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a9cf-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a9cf-121">Requirements</span></span>  
 <span data-ttu-id="9a9cf-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a9cf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a9cf-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a9cf-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a9cf-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a9cf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a9cf-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a9cf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9cf-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a9cf-126">See Also</span></span>  
 [<span data-ttu-id="9a9cf-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a9cf-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9a9cf-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a9cf-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9a9cf-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a9cf-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [<span data-ttu-id="9a9cf-130">GetModuleInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a9cf-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
