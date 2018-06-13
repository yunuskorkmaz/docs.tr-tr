---
title: ICorProfilerInfo::GetInprocInspectionIThisThread Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d603d9bc7a343a41224cf8d889a69823875d9db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453596"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="ef424-102">ICorProfilerInfo::GetInprocInspectionIThisThread Metodu</span><span class="sxs-lookup"><span data-stu-id="ef424-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="ef424-103">Icordebugthread arabirimi için sorgulanabilir bir nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="ef424-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="ef424-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef424-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef424-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef424-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef424-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef424-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="ef424-107">[out](/cpp/atl/iunknown) için sorgulanan nesne `ICorDebugThread` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ef424-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef424-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef424-108">Remarks</span></span>  
 <span data-ttu-id="ef424-109">Sınırlı işlem içi .NET Framework sürüm 1.0 debugging hizmetlerinde hata ayıklama ortak dil çalışma zamanı (CLR) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ef424-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="ef424-110">İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="ef424-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="ef424-111">Müşteri geri bildirimi sonucu olarak, işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="ef424-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef424-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef424-112">Requirements</span></span>  
 <span data-ttu-id="ef424-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef424-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef424-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef424-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef424-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef424-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef424-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="ef424-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef424-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef424-117">See Also</span></span>  
 [<span data-ttu-id="ef424-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef424-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
