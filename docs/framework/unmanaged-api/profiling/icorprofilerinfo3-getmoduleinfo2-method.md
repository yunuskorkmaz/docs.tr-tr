---
title: ICorProfilerInfo3::GetModuleInfo2 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fadca931ca4a57c83257f24e34e847870c9f493
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040969"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="aaea8-102">ICorProfilerInfo3::GetModuleInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="aaea8-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="aaea8-103">Derleme ve modül özelliklerini açıklayan bir bit maskesi, bir modül kimliği modül, modülün üst kimliği dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="aaea8-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaea8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aaea8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="aaea8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aaea8-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="aaea8-106">[in] Bilgileri alınır modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="aaea8-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="aaea8-107">[out] Modülün yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="aaea8-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="aaea8-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="aaea8-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="aaea8-109">[out] Bir işaretçi döndürülür modülün dosya adının toplam karakter uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="aaea8-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="aaea8-110">[out] Bir çağıran tarafından sağlanan geniş karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="aaea8-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="aaea8-111">Yöntem döndürüldüğünde bu arabellek modülü dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="aaea8-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="aaea8-112">[out] Modülün üst derleme kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aaea8-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="aaea8-113">[out] Bir bit maskesi değerleri [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) modülü özelliklerini belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="aaea8-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaea8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaea8-114">Remarks</span></span>  
 <span data-ttu-id="aaea8-115">Dinamik modüller için `szName` modülü meta veri adı bir parametredir ve 0 (sıfır) taban adresidir.</span><span class="sxs-lookup"><span data-stu-id="aaea8-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="aaea8-116">Meta veri değeri meta verileri içinde modül tablosundaki Ad sütununda addır.</span><span class="sxs-lookup"><span data-stu-id="aaea8-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="aaea8-117">Bu ayrıca olarak gösterilir <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> özelliği yönetilen koda ve olarak `szName` parametresinin [Imetadataımport::getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) yöntemi yönetilmeyen meta veriler istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="aaea8-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="aaea8-118">Ancak `GetModuleInfo2` yöntemi çağrıldığında modülün kimliği var. hemen sonra Profil Oluşturucu alıncaya kadar üst derlemesinin kimliği kullanılabilir olmayacak [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="aaea8-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="aaea8-119">Zaman `GetModuleInfo2` döndürür, doğrulamalısınız `szName` arabellek modülün tam dosya adını içerecek şekilde büyük.</span><span class="sxs-lookup"><span data-stu-id="aaea8-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="aaea8-120">Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="aaea8-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="aaea8-121">Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetModuleInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="aaea8-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="aaea8-122">Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo2` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="aaea8-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="aaea8-123">Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcchName` ve çağrı `GetModuleInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="aaea8-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaea8-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aaea8-124">Requirements</span></span>  
 <span data-ttu-id="aaea8-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaea8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaea8-126">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aaea8-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aaea8-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaea8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaea8-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaea8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaea8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaea8-129">See also</span></span>

- [<span data-ttu-id="aaea8-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaea8-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="aaea8-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aaea8-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="aaea8-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aaea8-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
