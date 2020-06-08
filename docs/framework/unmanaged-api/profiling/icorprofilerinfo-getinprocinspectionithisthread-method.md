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
ms.openlocfilehash: 0a4cb365ca8f7d52be505368a3d769a9728983bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502970"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="c813f-102">ICorProfilerInfo::GetInprocInspectionIThisThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c813f-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="c813f-103">ICorDebugThread arabirimi için sorgulanabilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="c813f-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="c813f-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c813f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c813f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c813f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c813f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c813f-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="c813f-107">arabirim için sorgulanabilen [Çıkış](/cpp/atl/iunknown) nesnesi `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="c813f-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c813f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c813f-108">Remarks</span></span>  
 <span data-ttu-id="c813f-109">Ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri, .NET Framework sürüm 1,0 ' de sınırlı sayıda işlem hata ayıklamayı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="c813f-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="c813f-110">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="c813f-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="c813f-111">Müşteri geri bildirimlerinden kaynaklanan işlem içi hata ayıklama, 2,0 sürümündeki .NET Framework kaldırılmıştır ve profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c813f-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c813f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c813f-112">Requirements</span></span>  
 <span data-ttu-id="c813f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c813f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c813f-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c813f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c813f-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c813f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c813f-116">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="c813f-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c813f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c813f-117">See also</span></span>

- [<span data-ttu-id="c813f-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c813f-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
