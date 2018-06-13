---
title: ICorProfilerInfo::GetInprocInspectionInterface Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 761dd55d2ae48739f24a03b8ce81c571fb211a5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453163"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="cf84d-102">ICorProfilerInfo::GetInprocInspectionInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="cf84d-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="cf84d-103">Sorgulanabilir bir nesne için bir "ICorDebugProcess" arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="cf84d-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="cf84d-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf84d-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf84d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf84d-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf84d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf84d-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="cf84d-107">[out](/cpp/atl/iunknown) için sorgulanan nesne bir `ICorDebugProcess` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cf84d-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf84d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf84d-108">Remarks</span></span>  
 <span data-ttu-id="cf84d-109">Hata ayıklama API'si ortak dil çalışma zamanı (CLR), sınırlı işlem içi .NET Framework sürüm 1.0 debugging desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cf84d-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="cf84d-110">İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="cf84d-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="cf84d-111">Müşteri geri bildirimi sonucu olarak, işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="cf84d-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf84d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf84d-112">Requirements</span></span>  
 <span data-ttu-id="cf84d-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf84d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf84d-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf84d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf84d-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf84d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf84d-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="cf84d-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf84d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf84d-117">See Also</span></span>  
 [<span data-ttu-id="cf84d-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf84d-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
