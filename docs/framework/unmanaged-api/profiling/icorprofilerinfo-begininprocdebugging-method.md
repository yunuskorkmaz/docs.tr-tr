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
ms.openlocfilehash: 3f56c3faa10eb05896936a37b0094797b0b6e2b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669178"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="c62a9-102">ICorProfilerInfo::BeginInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c62a9-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>

<span data-ttu-id="c62a9-103">İşlem içi hata ayıklama desteğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="c62a9-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="c62a9-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c62a9-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c62a9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c62a9-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c62a9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c62a9-106">Parameters</span></span>  

 `fThisThreadOnly`  
 <span data-ttu-id="c62a9-107">'ndaki `true` Yalnızca geçerli iş parçacığı için hata ayıklama desteğini başlatmak üzere bu değeri olarak ayarlayın; `false` tüm iş parçacıkları için hata ayıklama desteğini başlatacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c62a9-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="c62a9-108">dışı Hata ayıklama oturumunu tanımlayan döndürülen değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c62a9-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c62a9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c62a9-109">Remarks</span></span>  

 <span data-ttu-id="c62a9-110">CLR hata ayıklama Hizmetleri, 1,0 ve 1,1 .NET Framework sürümlerinde sınırlı sayıda işlem hata ayıklamayı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="c62a9-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="c62a9-111">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="c62a9-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="c62a9-112">Bununla birlikte, müşteri geri bildirimleri nedeniyle işlem içi hata ayıklama 2,0 sürümündeki .NET Framework kaldırılmıştır ve, profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c62a9-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c62a9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c62a9-113">Requirements</span></span>  

 <span data-ttu-id="c62a9-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c62a9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c62a9-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c62a9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c62a9-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c62a9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c62a9-117">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="c62a9-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62a9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c62a9-118">See also</span></span>

- [<span data-ttu-id="c62a9-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c62a9-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
