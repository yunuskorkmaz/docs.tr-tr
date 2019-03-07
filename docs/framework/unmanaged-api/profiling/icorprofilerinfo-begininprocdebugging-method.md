---
title: ICorProfilerInfo::BeginInprocDebugging Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e23f39f8e7a1812366e15ffec9589f756c73f94
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481696"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="69707-102">ICorProfilerInfo::BeginInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69707-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="69707-103">Başlatır-hata ayıklama desteği işlem.</span><span class="sxs-lookup"><span data-stu-id="69707-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="69707-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="69707-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69707-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69707-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69707-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69707-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="69707-107">[in] Bu değer kümesine `true` yalnızca geçerli iş parçacığı için; hata ayıklama desteği başlatılamıyor ayarlayın `false` tüm iş parçacıkları için hata ayıklama desteği başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="69707-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="69707-108">[out] Hata ayıklama oturumunu tanımlayan döndürülen değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="69707-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69707-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69707-109">Remarks</span></span>  
 <span data-ttu-id="69707-110">CLR hata ayıklama Hizmetleri .NET Framework sürüm 1.0 ve 1.1 debugging işlemdeki sınırlı desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="69707-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="69707-111">İşlem içi hata ayıklama, hata ayıklama API incelemesi bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="69707-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="69707-112">Ancak, müşteri geri bildirimi nedeniyle, işlemdeki hata ayıklama olduğundan .NET Framework sürüm 2. 0'dan Kaldırılan ve profil oluşturma API'ayarlarına uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="69707-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69707-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69707-113">Requirements</span></span>  
 <span data-ttu-id="69707-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69707-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69707-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69707-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69707-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69707-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69707-117">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="69707-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69707-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69707-118">See also</span></span>
- [<span data-ttu-id="69707-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69707-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
