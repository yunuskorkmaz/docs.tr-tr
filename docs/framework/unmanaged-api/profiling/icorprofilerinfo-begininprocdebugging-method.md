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
ms.openlocfilehash: c14979fa711145b9f1a134f90d7450b24e6d8a15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864303"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="9d0ea-102">ICorProfilerInfo::BeginInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d0ea-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="9d0ea-103">İşlem içi hata ayıklama desteğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="9d0ea-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0ea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d0ea-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d0ea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d0ea-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="9d0ea-107">'ndaki Yalnızca geçerli iş parçacığı için hata ayıklama desteğini başlatmak üzere bu değeri `true` olarak ayarlayın; Tüm iş parçacıkları için hata ayıklama desteğini başlatmak üzere `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="9d0ea-108">dışı Hata ayıklama oturumunu tanımlayan döndürülen değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d0ea-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d0ea-109">Remarks</span></span>  
 <span data-ttu-id="9d0ea-110">CLR hata ayıklama Hizmetleri, 1,0 ve 1,1 .NET Framework sürümlerinde sınırlı sayıda işlem hata ayıklamayı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="9d0ea-111">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="9d0ea-112">Bununla birlikte, müşteri geri bildirimleri nedeniyle işlem içi hata ayıklama 2,0 sürümündeki .NET Framework kaldırılmıştır ve, profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d0ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d0ea-113">Requirements</span></span>  
 <span data-ttu-id="9d0ea-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d0ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d0ea-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d0ea-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d0ea-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d0ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d0ea-117">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="9d0ea-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0ea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d0ea-118">See also</span></span>

- [<span data-ttu-id="9d0ea-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d0ea-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
