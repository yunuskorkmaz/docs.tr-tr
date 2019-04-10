---
title: ICorProfilerInfo::GetInprocInspectionIThisThread Yöntemi
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
ms.openlocfilehash: 24b7af4b44d51da06e9d65104f1b469ef1d83b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219440"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="328a0-102">ICorProfilerInfo::GetInprocInspectionIThisThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="328a0-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="328a0-103">Icordebugthread arabirimi sorgulanabilir bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="328a0-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="328a0-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="328a0-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="328a0-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="328a0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="328a0-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="328a0-107">[Çıkış](/cpp/atl/iunknown) için sorgulanan nesne `ICorDebugThread` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="328a0-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="328a0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="328a0-108">Remarks</span></span>  
 <span data-ttu-id="328a0-109">.NET Framework sürüm 1.0 debugging işlemdeki sınırlı hata ayıklama Hizmetleri ortak dil çalışma zamanı (CLR) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="328a0-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="328a0-110">İşlem içi hata ayıklama, hata ayıklama API incelemesi bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="328a0-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="328a0-111">Müşteri geri bildirim sonucunda, işlemdeki hata ayıklama algıladı .NET Framework sürüm 2. 0'dan kaldırılmadığı ve profil oluşturma API'ayarlarına uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="328a0-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="328a0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="328a0-112">Requirements</span></span>  
 <span data-ttu-id="328a0-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328a0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328a0-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="328a0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="328a0-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="328a0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="328a0-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="328a0-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328a0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="328a0-117">See also</span></span>

- [<span data-ttu-id="328a0-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="328a0-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
