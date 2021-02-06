---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo:: Getınprocinspectionithısthread yöntemi'
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
ms.openlocfilehash: 07ff904170750976e54e623101a2552db0c7f290
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647251"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="7768b-103">ICorProfilerInfo::GetInprocInspectionIThisThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7768b-103">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>

<span data-ttu-id="7768b-104">ICorDebugThread arabirimi için sorgulanabilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="7768b-104">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="7768b-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7768b-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7768b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7768b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7768b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7768b-107">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="7768b-108">arabirim için sorgulanabilen [Çıkış](/cpp/atl/iunknown) nesnesi `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="7768b-108">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7768b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7768b-109">Remarks</span></span>  

 <span data-ttu-id="7768b-110">Ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri, .NET Framework sürüm 1,0 ' de sınırlı sayıda işlem hata ayıklamayı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="7768b-110">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="7768b-111">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="7768b-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="7768b-112">Müşteri geri bildirimlerinden kaynaklanan işlem içi hata ayıklama, 2,0 sürümündeki .NET Framework kaldırılmıştır ve profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7768b-112">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7768b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7768b-113">Requirements</span></span>  

 <span data-ttu-id="7768b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7768b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7768b-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7768b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7768b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7768b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7768b-117">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="7768b-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7768b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7768b-118">See also</span></span>

- [<span data-ttu-id="7768b-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7768b-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
