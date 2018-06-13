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
ms.openlocfilehash: 82e798e1a31f771c63e71f2a85f8cbb684b237bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462396"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="ac345-102">ICorProfilerInfo::BeginInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac345-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="ac345-103">Başlatır hata ayıklama desteği işlemdeki.</span><span class="sxs-lookup"><span data-stu-id="ac345-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="ac345-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="ac345-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac345-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac345-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac345-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac345-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="ac345-107">[in] Bu değer ayarlanırsa `true` yalnızca geçerli iş parçacığının için; hata ayıklama desteği başlatılamıyor ayarlamak `false` tüm iş parçacıklarının hata ayıklama desteği başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ac345-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="ac345-108">[out] Hata ayıklama oturumu tanımlayan döndürülen değer yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac345-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac345-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac345-109">Remarks</span></span>  
 <span data-ttu-id="ac345-110">CLR hata ayıklama hizmetleri sınırlı işlemdeki .NET Framework sürüm 1.0 ve 1.1 debugging desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ac345-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="ac345-111">İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="ac345-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="ac345-112">Ancak, müşteri geri bildirimi nedeniyle işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="ac345-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac345-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac345-113">Requirements</span></span>  
 <span data-ttu-id="ac345-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac345-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac345-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac345-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac345-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac345-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac345-117">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="ac345-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac345-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac345-118">See Also</span></span>  
 [<span data-ttu-id="ac345-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac345-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
