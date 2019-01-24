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
ms.openlocfilehash: 019a85d6d58c99adb7c16be5cc3b31b029b0312d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513158"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="0b51f-102">ICorProfilerInfo::GetInprocInspectionIThisThread Metodu</span><span class="sxs-lookup"><span data-stu-id="0b51f-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="0b51f-103">Icordebugthread arabirimi sorgulanabilir bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="0b51f-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="0b51f-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0b51f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b51f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b51f-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b51f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b51f-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="0b51f-107">[Çıkış](/cpp/atl/iunknown) için sorgulanan nesne `ICorDebugThread` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0b51f-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b51f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b51f-108">Remarks</span></span>  
 <span data-ttu-id="0b51f-109">.NET Framework sürüm 1.0 debugging işlemdeki sınırlı hata ayıklama Hizmetleri ortak dil çalışma zamanı (CLR) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0b51f-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="0b51f-110">İşlem içi hata ayıklama, hata ayıklama API incelemesi bölümlerini kullanmak bir profil oluşturucu etkin.</span><span class="sxs-lookup"><span data-stu-id="0b51f-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="0b51f-111">Müşteri geri bildirim sonucunda, işlemdeki hata ayıklama algıladı .NET Framework sürüm 2. 0'dan kaldırılmadığı ve profil oluşturma API'ayarlarına uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="0b51f-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b51f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b51f-112">Requirements</span></span>  
 <span data-ttu-id="0b51f-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b51f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b51f-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b51f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b51f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b51f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b51f-116">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="0b51f-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b51f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b51f-117">See also</span></span>
- [<span data-ttu-id="0b51f-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b51f-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
