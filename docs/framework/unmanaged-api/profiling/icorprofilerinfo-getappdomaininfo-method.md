---
description: ': ICorProfilerInfo:: GetAppDomainInfo yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 981577320bdf04a2bf119115f066811d3c11b68f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687291"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="71311-103">ICorProfilerInfo::GetAppDomainInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71311-103">ICorProfilerInfo::GetAppDomainInfo Method</span></span>

<span data-ttu-id="71311-104">Bir uygulama etki alanı KIMLIĞINI kabul eder.</span><span class="sxs-lookup"><span data-stu-id="71311-104">Accepts an application domain ID.</span></span> <span data-ttu-id="71311-105">Bir uygulama etki alanı adı ve onu içeren işlemin KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="71311-105">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71311-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71311-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71311-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71311-107">Parameters</span></span>  

 `appDomainId`  
 <span data-ttu-id="71311-108">'ndaki Uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="71311-108">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="71311-109">'ndaki Dönüş arabelleğinin karakter cinsinden uzunluğu `szName` .</span><span class="sxs-lookup"><span data-stu-id="71311-109">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="71311-110">dışı Uygulama etki alanı adının toplam karakter uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71311-110">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="71311-111">dışı Arayan tarafından sunulan geniş bir karakter arabelleği.</span><span class="sxs-lookup"><span data-stu-id="71311-111">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="71311-112">Yöntemi döndüğünde, `szName` tam veya kısmi uygulama etki alanı adını içerecektir.</span><span class="sxs-lookup"><span data-stu-id="71311-112">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="71311-113">dışı Uygulama etki alanını içeren işlemin KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71311-113">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71311-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71311-114">Remarks</span></span>  

 <span data-ttu-id="71311-115">Bu yöntem geri döndüğünde, `szName` arabelleğin uygulama etki alanının tam adını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="71311-115">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="71311-116">Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` .</span><span class="sxs-lookup"><span data-stu-id="71311-116">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="71311-117">Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetAppDomainInfo` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="71311-117">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="71311-118">Alternatif olarak, `GetAppDomainInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71311-118">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="71311-119">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcchName` ve `GetAppDomainInfo` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71311-119">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71311-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71311-120">Requirements</span></span>  

 <span data-ttu-id="71311-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71311-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71311-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="71311-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71311-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="71311-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71311-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71311-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71311-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71311-125">See also</span></span>

- [<span data-ttu-id="71311-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71311-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="71311-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71311-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="71311-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="71311-128">Profiling</span></span>](index.md)
