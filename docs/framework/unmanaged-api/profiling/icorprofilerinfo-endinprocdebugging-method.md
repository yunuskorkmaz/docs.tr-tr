---
title: ICorProfilerInfo::EndInprocDebugging Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: 09b1b81bde486db67acede99e0d67ff85cb01bae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447759"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="7a150-102">ICorProfilerInfo::EndInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a150-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="7a150-103">İşlem içi hata ayıklama oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="7a150-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="7a150-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7a150-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a150-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a150-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a150-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a150-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="7a150-107">'ndaki Hata ayıklama oturumunu tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="7a150-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="7a150-108">Bu değer [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) yönteminde alınan ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a150-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a150-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a150-109">Remarks</span></span>  
 <span data-ttu-id="7a150-110">[ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) ve `EndInprocDebugging` aynı geri çağırma yöntemi içinde çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a150-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="7a150-111">CLR hata ayıklama Hizmetleri, 1,0 ve 1,1 .NET Framework sürümlerinde sınırlı sayıda işlem hata ayıklamayı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="7a150-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="7a150-112">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="7a150-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="7a150-113">Bununla birlikte, müşteri geri bildirimleri nedeniyle işlem içi hata ayıklama 2,0 sürümündeki .NET Framework kaldırılmıştır ve, profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a150-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a150-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a150-114">Requirements</span></span>  
 <span data-ttu-id="7a150-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a150-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a150-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7a150-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a150-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7a150-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a150-118">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="7a150-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a150-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a150-119">See also</span></span>

- [<span data-ttu-id="7a150-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a150-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
