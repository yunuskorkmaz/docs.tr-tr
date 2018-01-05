---
title: ICorProfilerInfo::GetInprocInspectionInterface Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionInterface
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type: apiref
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9088389df33b079fe2275f5c7e642a055fa8ee51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="6f81b-102">ICorProfilerInfo::GetInprocInspectionInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="6f81b-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="6f81b-103">Sorgulanabilir bir nesne için bir "ICorDebugProcess" arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="6f81b-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="6f81b-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f81b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f81b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f81b-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f81b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f81b-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="6f81b-107">[out](/cpp/atl/iunknown) için sorgulanan nesne bir `ICorDebugProcess` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6f81b-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f81b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f81b-108">Remarks</span></span>  
 <span data-ttu-id="6f81b-109">Hata ayıklama API'si ortak dil çalışma zamanı (CLR), sınırlı işlem içi .NET Framework sürüm 1.0 debugging desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6f81b-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="6f81b-110">İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="6f81b-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="6f81b-111">Müşteri geri bildirimi sonucu olarak, işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="6f81b-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f81b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f81b-112">Requirements</span></span>  
 <span data-ttu-id="6f81b-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f81b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f81b-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f81b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f81b-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f81b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f81b-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="6f81b-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f81b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f81b-117">See Also</span></span>  
 [<span data-ttu-id="6f81b-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f81b-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
