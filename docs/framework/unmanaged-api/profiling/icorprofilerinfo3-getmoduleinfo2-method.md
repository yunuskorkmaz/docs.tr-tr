---
title: ICorProfilerInfo3::GetModuleInfo2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetModuleInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b891f55ab79d32814f44eabf50343aa113b0835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="d4501-102">ICorProfilerInfo3::GetModuleInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="d4501-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="d4501-103">Modül kimliği derleme ve modül özelliklerini açıklayan bir bit maskesi modül, modülün üst Kimliğini dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4501-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4501-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4501-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4501-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4501-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d4501-106">[in] Bilgiler alınır modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="d4501-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="d4501-107">[out] Modül yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="d4501-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d4501-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabellek.</span><span class="sxs-lookup"><span data-stu-id="d4501-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d4501-109">[out] Toplam karakter uzunluğu döndürülen modülün dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4501-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="d4501-110">[out] Çağıran tarafından sağlanan geniş karakter arabellek.</span><span class="sxs-lookup"><span data-stu-id="d4501-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="d4501-111">Yöntem döndüğünde, bu arabellek modülü dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="d4501-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="d4501-112">[out] Modülün üst derleme kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4501-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="d4501-113">[out] Bir bit maskesi değerleri [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) modülü özelliklerini belirtin numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d4501-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4501-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4501-114">Remarks</span></span>  
 <span data-ttu-id="d4501-115">Dinamik modülleri için `szName` parametresi modülün meta veri adı ve temel adres 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="d4501-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="d4501-116">Meta verileri, meta veri içindeki modül tablosundan adı sütunundaki değeri adıdır.</span><span class="sxs-lookup"><span data-stu-id="d4501-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="d4501-117">Bu ayrıca olarak sunulan <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> özelliği yönetilen kod için ve olarak `szName` parametresinin [Imetadataımport::getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) yönetilmeyen meta veriler istemci kodu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4501-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="d4501-118">Ancak `GetModuleInfo2` modülün kimliği var hemen yöntemi'nin çağrılabilir, profil oluşturucu alıncaya kadar üst derleme Kimliğini kullanılamaz [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="d4501-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="d4501-119">Zaman `GetModuleInfo2` döndürür, doğrulamalısınız `szName` arabellek modülü tam dosya adını içerecek kadar büyük.</span><span class="sxs-lookup"><span data-stu-id="d4501-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="d4501-120">Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d4501-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d4501-121">Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetModuleInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="d4501-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="d4501-122">Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo2` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="d4501-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d4501-123">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetModuleInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="d4501-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4501-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4501-124">Requirements</span></span>  
 <span data-ttu-id="d4501-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4501-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4501-126">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4501-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4501-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4501-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4501-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4501-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4501-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4501-129">See Also</span></span>  
 [<span data-ttu-id="d4501-130">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4501-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="d4501-131">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4501-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d4501-132">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4501-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
