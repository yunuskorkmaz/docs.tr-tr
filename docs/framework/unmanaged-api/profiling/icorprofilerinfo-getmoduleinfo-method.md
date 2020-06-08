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
ms.openlocfilehash: 751f2ac44e543fed76c7031791bb57d75ed0fd48
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498108"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="db312-102">ICorProfilerInfo::GetModuleInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db312-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="db312-103">Bir modül KIMLIĞI verildiğinde, modülün dosya adını ve modülün üst derleme KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="db312-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db312-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="db312-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="db312-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db312-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="db312-106">'ndaki Bilgilerin alınacağı modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="db312-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="db312-107">dışı Modülün yüklendiği temel adres.</span><span class="sxs-lookup"><span data-stu-id="db312-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="db312-108">'ndaki Dönüş arabelleğinin karakter cinsinden uzunluğu `szName` .</span><span class="sxs-lookup"><span data-stu-id="db312-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="db312-109">dışı Modülün dosya adının döndürülen toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db312-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="db312-110">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="db312-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="db312-111">Yöntem döndüğünde, bu arabellek modülün dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="db312-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="db312-112">dışı Modülün üst derleme KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db312-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db312-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db312-113">Remarks</span></span>  
 <span data-ttu-id="db312-114">Dinamik modüller için `szName` parametresi boş bir dizedir ve temel adres 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="db312-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="db312-115">`GetModuleInfo`Yöntemi modülün kimliği mevcut olduğu anda çağrılabilir olsa da, ana DERLEMENIN kimliği, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="db312-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="db312-116">`GetModuleInfo`' İ döndüğünde, `szName` arabelleğin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db312-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="db312-117">Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="db312-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="db312-118">Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetModuleInfo` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="db312-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="db312-119">Alternatif olarak, `GetModuleInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db312-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="db312-120">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcchName` ve `GetModuleInfo` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db312-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db312-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db312-121">Requirements</span></span>  
 <span data-ttu-id="db312-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db312-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db312-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="db312-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db312-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="db312-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db312-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db312-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db312-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db312-126">See also</span></span>

- [<span data-ttu-id="db312-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db312-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="db312-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="db312-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="db312-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db312-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="db312-130">GetModuleInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db312-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
