---
title: ICorProfilerInfo::GetAppDomainInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c31d3c61a868bf741213f6e505d91524cc925207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="96eeb-102">ICorProfilerInfo::GetAppDomainInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="96eeb-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="96eeb-103">Bir uygulama etki alanı kimliği kabul eder</span><span class="sxs-lookup"><span data-stu-id="96eeb-103">Accepts an application domain ID.</span></span> <span data-ttu-id="96eeb-104">Uygulama etki alanı adını ve içerdiği işlem Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="96eeb-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96eeb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96eeb-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96eeb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96eeb-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="96eeb-107">[in] Uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="96eeb-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="96eeb-108">[in] Karakter cinsinden uzunluğu, `szName` dönüş arabellek.</span><span class="sxs-lookup"><span data-stu-id="96eeb-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="96eeb-109">[out] Uygulama etki alanı adının toplam karakter uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96eeb-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="96eeb-110">[out] Çağıran tarafından sağlanan geniş karakter arabellek.</span><span class="sxs-lookup"><span data-stu-id="96eeb-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="96eeb-111">Yöntem döndüğünde `szName` tam veya kısmi uygulama etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="96eeb-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="96eeb-112">[out] Uygulama etki alanını içeren işlem kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96eeb-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96eeb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96eeb-113">Remarks</span></span>  
 <span data-ttu-id="96eeb-114">Bu yöntem döndükten sonra doğrulamanız gerekir `szName` arabellek uygulama etki alanının tam adını içerecek kadar büyük.</span><span class="sxs-lookup"><span data-stu-id="96eeb-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="96eeb-115">Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="96eeb-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="96eeb-116">Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetAppDomainInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="96eeb-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="96eeb-117">Alternatif olarak, ilk çağırabilirsiniz `GetAppDomainInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="96eeb-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="96eeb-118">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetAppDomainInfo` yeniden.</span><span class="sxs-lookup"><span data-stu-id="96eeb-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96eeb-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96eeb-119">Requirements</span></span>  
 <span data-ttu-id="96eeb-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96eeb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96eeb-121">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96eeb-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96eeb-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96eeb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96eeb-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96eeb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96eeb-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96eeb-124">See Also</span></span>  
 [<span data-ttu-id="96eeb-125">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="96eeb-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="96eeb-126">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96eeb-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="96eeb-127">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="96eeb-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
