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
ms.openlocfilehash: d2b7e93866bf0aa79849925234a4d6e4cc9b5b52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502827"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="2756b-102">ICorProfilerInfo3::GetModuleInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="2756b-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="2756b-103">Modül KIMLIĞI verildiğinde, modülün dosya adını, modülün üst derleme KIMLIĞINI ve modülün özelliklerini açıklayan bir bit maskesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2756b-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2756b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2756b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="2756b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2756b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2756b-106">'ndaki Bilgilerin alınacağı modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2756b-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="2756b-107">dışı Modülün yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="2756b-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2756b-108">'ndaki Dönüş arabelleğinin karakter cinsinden uzunluğu `szName` .</span><span class="sxs-lookup"><span data-stu-id="2756b-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2756b-109">dışı Modülün dosya adının döndürülen toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2756b-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="2756b-110">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="2756b-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="2756b-111">Yöntem döndüğünde, bu arabellek modülün dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="2756b-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="2756b-112">dışı Modülün üst derleme KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2756b-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="2756b-113">dışı [Cor_prf_module_flags](cor-prf-module-flags-enumeration.md) Numaralandırmadaki, modülün özelliklerini belirten değerlerin bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="2756b-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2756b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2756b-114">Remarks</span></span>  
 <span data-ttu-id="2756b-115">Dinamik modüller için parametresi, `szName` modülün meta veri adıdır ve temel adres 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="2756b-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="2756b-116">Meta veri adı, meta veriler içindeki modül tablosundan Ad sütunundaki değerdir.</span><span class="sxs-lookup"><span data-stu-id="2756b-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="2756b-117">Bu, <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> yönetilen koda özellik olarak ve `szName` [IMetaDataImport:: GetScopeProps](../metadata/imetadataimport-getscopeprops-method.md) yönteminin parametresi olarak yönetilmeyen meta veri istemci koduna olarak da sunulur.</span><span class="sxs-lookup"><span data-stu-id="2756b-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="2756b-118">`GetModuleInfo2`Yöntemi modülün kimliği mevcut olduğu anda çağrılabilir olsa da, ana DERLEMENIN kimliği, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2756b-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="2756b-119">`GetModuleInfo2`' İ döndüğünde, `szName` arabelleğin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2756b-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="2756b-120">Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="2756b-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="2756b-121">Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetModuleInfo2` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="2756b-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="2756b-122">Alternatif olarak, `GetModuleInfo2` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2756b-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2756b-123">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcchName` ve `GetModuleInfo2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2756b-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2756b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2756b-124">Requirements</span></span>  
 <span data-ttu-id="2756b-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2756b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2756b-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2756b-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2756b-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2756b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2756b-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2756b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2756b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2756b-129">See also</span></span>

- [<span data-ttu-id="2756b-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2756b-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2756b-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2756b-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2756b-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2756b-132">Profiling</span></span>](index.md)
