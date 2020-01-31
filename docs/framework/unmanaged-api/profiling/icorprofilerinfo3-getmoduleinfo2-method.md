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
ms.openlocfilehash: 96cde35c7151bb7ce58715f2826feaa59b30efab
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862314"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="63420-102">ICorProfilerInfo3::GetModuleInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="63420-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="63420-103">Modül KIMLIĞI verildiğinde, modülün dosya adını, modülün üst derleme KIMLIĞINI ve modülün özelliklerini açıklayan bir bit maskesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="63420-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63420-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63420-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="63420-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63420-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="63420-106">'ndaki Bilgilerin alınacağı modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="63420-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="63420-107">dışı Modülün yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="63420-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="63420-108">'ndaki `szName` dönüş arabelleğinin karakter cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="63420-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="63420-109">dışı Modülün dosya adının döndürülen toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63420-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="63420-110">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="63420-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="63420-111">Yöntem döndüğünde, bu arabellek modülün dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="63420-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="63420-112">dışı Modülün üst derleme KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63420-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="63420-113">dışı [Cor_prf_module_flags](cor-prf-module-flags-enumeration.md) Numaralandırmadaki, modülün özelliklerini belirten değerlerin bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="63420-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63420-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63420-114">Remarks</span></span>  
 <span data-ttu-id="63420-115">Dinamik modüller için `szName` parametresi modülün meta veri adıdır ve temel adres 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="63420-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="63420-116">Meta veri adı, meta veriler içindeki modül tablosundan Ad sütunundaki değerdir.</span><span class="sxs-lookup"><span data-stu-id="63420-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="63420-117">Bu Ayrıca, yönetilen koda <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> özelliği olarak ve [IMetaDataImport:: GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) yönteminin `szName` parametresi olarak yönetilmeyen meta veri istemci koduna da sunulur.</span><span class="sxs-lookup"><span data-stu-id="63420-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="63420-118">`GetModuleInfo2` yöntemi modülün KIMLIĞI mevcut olduğu anda çağrılabilir olsa da, ana derlemenin KIMLIĞI, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="63420-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="63420-119">`GetModuleInfo2` döndüğünde, `szName` arabelleğinin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="63420-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="63420-120">Bunu yapmak için `pcchName` işaret eden değeri `cchName` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="63420-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="63420-121">`pcchName`, `cchName`daha büyük bir değere işaret ediyorsa, daha büyük bir `szName` arabelleği ayırın, yeni, daha büyük boyuttaki `cchName` güncelleştirin ve `GetModuleInfo2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="63420-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="63420-122">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetModuleInfo2` sıfır uzunluklu `szName` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63420-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="63420-123">Daha sonra arabellek boyutunu `pcchName` döndürülen değere ayarlayabilir ve `GetModuleInfo2` tekrar çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63420-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63420-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63420-124">Requirements</span></span>  
 <span data-ttu-id="63420-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63420-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63420-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="63420-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63420-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63420-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63420-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63420-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63420-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63420-129">See also</span></span>

- [<span data-ttu-id="63420-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63420-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="63420-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63420-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="63420-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63420-132">Profiling</span></span>](index.md)
