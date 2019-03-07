---
title: ICorProfilerInfo::GetInprocInspectionInterface Yöntemi
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
ms.openlocfilehash: fbb4aa43757df86037d9c883e76ee38cef5eeb86
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494434"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="12532-102">ICorProfilerInfo::GetInprocInspectionInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12532-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="12532-103">Sorgulanabilir bir nesne için bir "ICorDebugProcess" arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="12532-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="12532-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="12532-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12532-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12532-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12532-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12532-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="12532-107">[Çıkış](/cpp/atl/iunknown) için sorgulanan nesne bir `ICorDebugProcess` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="12532-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12532-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12532-108">Remarks</span></span>  
 <span data-ttu-id="12532-109">.NET Framework sürüm 1.0 debugging işlemdeki sınırlı hata ayıklama API'si ortak dil çalışma zamanı (CLR) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="12532-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="12532-110">İşlem içi hata ayıklama, hata ayıklama API incelemesi bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="12532-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="12532-111">Müşteri geri bildirim sonucunda, işlemdeki hata ayıklama algıladı .NET Framework sürüm 2. 0'dan kaldırılmadığı ve profil oluşturma API'ayarlarına uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="12532-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12532-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12532-112">Requirements</span></span>  
 <span data-ttu-id="12532-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12532-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12532-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12532-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12532-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12532-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12532-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="12532-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12532-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12532-117">See also</span></span>
- [<span data-ttu-id="12532-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12532-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
