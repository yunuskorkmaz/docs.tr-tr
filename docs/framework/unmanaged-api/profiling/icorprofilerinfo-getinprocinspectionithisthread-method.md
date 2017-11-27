---
title: ICorProfilerInfo::GetInprocInspectionIThisThread Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionIThisThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9a260143e36939f4201d7949f5783f80e5c20ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="cf509-102">ICorProfilerInfo::GetInprocInspectionIThisThread Metodu</span><span class="sxs-lookup"><span data-stu-id="cf509-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="cf509-103">Icordebugthread arabirimi için sorgulanabilir bir nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="cf509-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="cf509-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf509-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf509-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf509-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf509-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf509-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="cf509-107">[out](/cpp/atl/iunknown) için sorgulanan nesne `ICorDebugThread` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cf509-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf509-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf509-108">Remarks</span></span>  
 <span data-ttu-id="cf509-109">Sınırlı işlem içi .NET Framework sürüm 1.0 debugging hizmetlerinde hata ayıklama ortak dil çalışma zamanı (CLR) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cf509-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="cf509-110">İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="cf509-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="cf509-111">Müşteri geri bildirimi sonucu olarak, işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="cf509-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf509-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf509-112">Requirements</span></span>  
 <span data-ttu-id="cf509-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf509-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf509-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf509-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf509-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf509-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf509-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="cf509-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf509-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf509-117">See Also</span></span>  
 [<span data-ttu-id="cf509-118">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf509-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
