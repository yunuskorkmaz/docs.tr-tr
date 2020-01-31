---
title: ICorProfilerInfo::GetAppDomainInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864121"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="a628e-102">ICorProfilerInfo::GetAppDomainInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a628e-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="a628e-103">Bir uygulama etki alanı KIMLIĞINI kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a628e-103">Accepts an application domain ID.</span></span> <span data-ttu-id="a628e-104">Bir uygulama etki alanı adı ve onu içeren işlemin KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="a628e-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a628e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a628e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a628e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a628e-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="a628e-107">'ndaki Uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a628e-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a628e-108">'ndaki `szName` dönüş arabelleğinin karakter cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a628e-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a628e-109">dışı Uygulama etki alanı adının toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a628e-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="a628e-110">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="a628e-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="a628e-111">Yöntemi döndürüldüğünde, `szName` tam veya kısmi uygulama etki alanı adını içerecektir.</span><span class="sxs-lookup"><span data-stu-id="a628e-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="a628e-112">dışı Uygulama etki alanını içeren işlemin KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a628e-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a628e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a628e-113">Remarks</span></span>  
 <span data-ttu-id="a628e-114">Bu yöntem çağrıldıktan sonra, `szName` arabelleğinin uygulama etki alanının tam adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a628e-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="a628e-115">Bunu yapmak için `pcchName` işaret eden değeri `cchName` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="a628e-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a628e-116">`pcchName`, `cchName`daha büyük bir değere işaret ediyorsa, daha büyük bir `szName` arabelleği ayırın, yeni, daha büyük boyuttaki `cchName` güncelleştirin ve `GetAppDomainInfo` çağırın.</span><span class="sxs-lookup"><span data-stu-id="a628e-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="a628e-117">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetAppDomainInfo` sıfır uzunluklu `szName` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a628e-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a628e-118">Daha sonra arabellek boyutunu `pcchName` döndürülen değere ayarlayabilir ve `GetAppDomainInfo` tekrar çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a628e-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a628e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a628e-119">Requirements</span></span>  
 <span data-ttu-id="a628e-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a628e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a628e-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a628e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a628e-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a628e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a628e-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a628e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a628e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a628e-124">See also</span></span>

- [<span data-ttu-id="a628e-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a628e-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a628e-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a628e-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a628e-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a628e-127">Profiling</span></span>](index.md)
