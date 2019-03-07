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
ms.openlocfilehash: f86c680a10a3dcb1009b4f0cedd777ab9da5ac1f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501753"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="3dd6b-102">ICorProfilerInfo::EndInprocDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dd6b-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="3dd6b-103">Bir işlemde hata ayıklama oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="3dd6b-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd6b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dd6b-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dd6b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dd6b-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="3dd6b-107">[in] Hata ayıklama oturumunu tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="3dd6b-108">Bu değer, alınan aynı olmalıdır [Icorprofilerınfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd6b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dd6b-109">Remarks</span></span>  
 <span data-ttu-id="3dd6b-110">Çağırmalısınız [Icorprofilerınfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) ve `EndInprocDebugging` içinde aynı geri çağırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="3dd6b-111">CLR hata ayıklama Hizmetleri .NET Framework sürüm 1.0 ve 1.1 debugging işlemdeki sınırlı desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="3dd6b-112">İşlem içi hata ayıklama, hata ayıklama API incelemesi bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="3dd6b-113">Ancak, müşteri geri bildirimi nedeniyle, işlemdeki hata ayıklama olduğundan .NET Framework sürüm 2. 0'dan Kaldırılan ve profil oluşturma API'ayarlarına uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd6b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dd6b-114">Requirements</span></span>  
 <span data-ttu-id="3dd6b-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd6b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd6b-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3dd6b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3dd6b-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dd6b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dd6b-118">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="3dd6b-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd6b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dd6b-119">See also</span></span>
- [<span data-ttu-id="3dd6b-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dd6b-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
