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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83468e13e1e028b031c31791910c4dd2d792f232
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992127"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="64a8a-102">ICorProfilerInfo::GetAppDomainInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64a8a-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="64a8a-103">Bir uygulama etki alanı kimliği kabul eder</span><span class="sxs-lookup"><span data-stu-id="64a8a-103">Accepts an application domain ID.</span></span> <span data-ttu-id="64a8a-104">Bir uygulama etki alanı adı ve içerdiği işlem Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="64a8a-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a8a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64a8a-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a8a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64a8a-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="64a8a-107">[in] Uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="64a8a-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="64a8a-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="64a8a-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="64a8a-109">[out] Uygulama etki alanı adının toplam karakter uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64a8a-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="64a8a-110">[out] Bir çağıran tarafından sağlanan geniş karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="64a8a-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="64a8a-111">Yöntem döndürüldüğünde `szName` tam veya kısmi uygulama etki alanı adı içerir.</span><span class="sxs-lookup"><span data-stu-id="64a8a-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="64a8a-112">[out] Uygulama etki alanını içeren işlem kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64a8a-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64a8a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64a8a-113">Remarks</span></span>  
 <span data-ttu-id="64a8a-114">Bu yöntemin dönüşünün ardından doğrulamanız gerekir `szName` arabelleği, uygulama etki alanının tam adını içerecek şekilde büyük.</span><span class="sxs-lookup"><span data-stu-id="64a8a-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="64a8a-115">Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="64a8a-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="64a8a-116">Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetAppDomainInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="64a8a-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="64a8a-117">Alternatif olarak, ilk çağırabilirsiniz `GetAppDomainInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="64a8a-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="64a8a-118">Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcchName` ve çağrı `GetAppDomainInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="64a8a-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a8a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64a8a-119">Requirements</span></span>  
 <span data-ttu-id="64a8a-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a8a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a8a-121">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64a8a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64a8a-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64a8a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64a8a-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a8a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a8a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64a8a-124">See also</span></span>

- [<span data-ttu-id="64a8a-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64a8a-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="64a8a-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64a8a-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="64a8a-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="64a8a-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
