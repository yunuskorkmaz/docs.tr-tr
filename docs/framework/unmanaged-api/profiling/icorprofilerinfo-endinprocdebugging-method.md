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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf7e2e7de54b065f25f3a1873d760ab5051cc91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452617"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="572f8-102">ICorProfilerInfo::EndInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="572f8-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="572f8-103">İşlem içi hata ayıklama oturumu kapatır.</span><span class="sxs-lookup"><span data-stu-id="572f8-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="572f8-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="572f8-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="572f8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="572f8-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="572f8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="572f8-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="572f8-107">[in] Hata ayıklama oturumu tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="572f8-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="572f8-108">Bu değer, alınan aynı olmalıdır [Icorprofilerınfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="572f8-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="572f8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="572f8-109">Remarks</span></span>  
 <span data-ttu-id="572f8-110">Çağırmalısınız [Icorprofilerınfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) ve `EndInprocDebugging` içinde aynı geri çağırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="572f8-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="572f8-111">CLR hata ayıklama hizmetleri sınırlı işlemdeki .NET Framework sürüm 1.0 ve 1.1 debugging desteklenir.</span><span class="sxs-lookup"><span data-stu-id="572f8-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="572f8-112">İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="572f8-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="572f8-113">Ancak, müşteri geri bildirimi nedeniyle işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="572f8-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="572f8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="572f8-114">Requirements</span></span>  
 <span data-ttu-id="572f8-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="572f8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="572f8-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="572f8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="572f8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="572f8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="572f8-118">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="572f8-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572f8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="572f8-119">See Also</span></span>  
 [<span data-ttu-id="572f8-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="572f8-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
