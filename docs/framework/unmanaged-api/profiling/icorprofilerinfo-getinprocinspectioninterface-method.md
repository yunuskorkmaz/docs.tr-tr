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
ms.openlocfilehash: 2fe0b314f761cf3c7a3a926d40c69302d0ece000
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498095"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="7cb86-102">ICorProfilerInfo::GetInprocInspectionInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cb86-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="7cb86-103">Bir "ICorDebugProcess" arabirimi için sorgulanabilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="7cb86-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="7cb86-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7cb86-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb86-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7cb86-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cb86-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cb86-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="7cb86-107">bir arabirim için sorgulanabilen [Çıkış](/cpp/atl/iunknown) nesnesi `ICorDebugProcess` .</span><span class="sxs-lookup"><span data-stu-id="7cb86-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cb86-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cb86-108">Remarks</span></span>  
 <span data-ttu-id="7cb86-109">Ortak dil çalışma zamanı (CLR) hata ayıklama API 'SI .NET Framework 1,0 sürümünde sınırlı sayıda işlem hata ayıklaması destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="7cb86-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="7cb86-110">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="7cb86-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="7cb86-111">Müşteri geri bildirimlerinden kaynaklanan işlem içi hata ayıklama, 2,0 sürümündeki .NET Framework kaldırılmıştır ve profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7cb86-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb86-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cb86-112">Requirements</span></span>  
 <span data-ttu-id="7cb86-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb86-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb86-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7cb86-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cb86-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7cb86-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cb86-116">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="7cb86-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb86-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cb86-117">See also</span></span>

- [<span data-ttu-id="7cb86-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cb86-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
