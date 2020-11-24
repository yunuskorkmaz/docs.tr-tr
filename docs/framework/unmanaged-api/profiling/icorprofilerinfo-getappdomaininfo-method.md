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
ms.openlocfilehash: 62055a98197f5f8bd4cfc02e99891b83ef6341e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680306"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="61ef4-102">ICorProfilerInfo::GetAppDomainInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61ef4-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>

<span data-ttu-id="61ef4-103">Bir uygulama etki alanı KIMLIĞINI kabul eder.</span><span class="sxs-lookup"><span data-stu-id="61ef4-103">Accepts an application domain ID.</span></span> <span data-ttu-id="61ef4-104">Bir uygulama etki alanı adı ve onu içeren işlemin KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="61ef4-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ef4-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="61ef4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ef4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61ef4-106">Parameters</span></span>  

 `appDomainId`  
 <span data-ttu-id="61ef4-107">'ndaki Uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="61ef4-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="61ef4-108">'ndaki Dönüş arabelleğinin karakter cinsinden uzunluğu `szName` .</span><span class="sxs-lookup"><span data-stu-id="61ef4-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="61ef4-109">dışı Uygulama etki alanı adının toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61ef4-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="61ef4-110">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="61ef4-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="61ef4-111">Yöntemi döndüğünde, `szName` tam veya kısmi uygulama etki alanı adını içerecektir.</span><span class="sxs-lookup"><span data-stu-id="61ef4-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="61ef4-112">dışı Uygulama etki alanını içeren işlemin KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61ef4-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61ef4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61ef4-113">Remarks</span></span>  

 <span data-ttu-id="61ef4-114">Bu yöntem geri döndüğünde, `szName` arabelleğin uygulama etki alanının tam adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61ef4-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="61ef4-115">Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="61ef4-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="61ef4-116">Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetAppDomainInfo` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="61ef4-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="61ef4-117">Alternatif olarak, `GetAppDomainInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61ef4-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="61ef4-118">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcchName` ve `GetAppDomainInfo` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61ef4-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ef4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61ef4-119">Requirements</span></span>  

 <span data-ttu-id="61ef4-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ef4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ef4-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="61ef4-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61ef4-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="61ef4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ef4-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ef4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ef4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61ef4-124">See also</span></span>

- [<span data-ttu-id="61ef4-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61ef4-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="61ef4-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="61ef4-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="61ef4-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61ef4-127">Profiling</span></span>](index.md)
