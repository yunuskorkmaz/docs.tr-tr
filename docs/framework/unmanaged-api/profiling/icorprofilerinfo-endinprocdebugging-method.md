---
description: ': ICorProfilerInfo:: Enınprocdebugging yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5e172abaa99e0a64031a9c1ec1beac5f23386d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788624"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="e623b-103">ICorProfilerInfo::EndInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e623b-103">ICorProfilerInfo::EndInprocDebugging Method</span></span>

<span data-ttu-id="e623b-104">İşlem içi hata ayıklama oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="e623b-104">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="e623b-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e623b-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e623b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e623b-106">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e623b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e623b-107">Parameters</span></span>  

 `dwProfilerContext`  
 <span data-ttu-id="e623b-108">'ndaki Hata ayıklama oturumunu tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="e623b-108">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="e623b-109">Bu değer [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) yönteminde alınan ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e623b-109">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e623b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e623b-110">Remarks</span></span>  

 <span data-ttu-id="e623b-111">[ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) ve `EndInprocDebugging` aynı geri arama yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e623b-111">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="e623b-112">CLR hata ayıklama Hizmetleri, 1,0 ve 1,1 .NET Framework sürümlerinde sınırlı sayıda işlem hata ayıklamayı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="e623b-112">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="e623b-113">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="e623b-113">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="e623b-114">Bununla birlikte, müşteri geri bildirimleri nedeniyle işlem içi hata ayıklama 2,0 sürümündeki .NET Framework kaldırılmıştır ve, profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e623b-114">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e623b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e623b-115">Requirements</span></span>  

 <span data-ttu-id="e623b-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e623b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e623b-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e623b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e623b-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e623b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e623b-119">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="e623b-119">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e623b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e623b-120">See also</span></span>

- [<span data-ttu-id="e623b-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e623b-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
