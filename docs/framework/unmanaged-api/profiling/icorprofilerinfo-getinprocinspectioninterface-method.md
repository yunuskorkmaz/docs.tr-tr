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
ms.openlocfilehash: d3fcd859fb11f6a0c660751f16fa175e19e9d03b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438999"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="4cc41-102">ICorProfilerInfo::GetInprocInspectionInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cc41-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="4cc41-103">Bir "ICorDebugProcess" arabirimi için sorgulanabilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="4cc41-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="4cc41-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="4cc41-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc41-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cc41-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cc41-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cc41-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="4cc41-107">`ICorDebugProcess` arabirimi için sorgulanabilen [Çıkış](/cpp/atl/iunknown) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4cc41-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cc41-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cc41-108">Remarks</span></span>  
 <span data-ttu-id="4cc41-109">Ortak dil çalışma zamanı (CLR) hata ayıklama API 'SI .NET Framework 1,0 sürümünde sınırlı sayıda işlem hata ayıklaması destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="4cc41-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="4cc41-110">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="4cc41-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="4cc41-111">Müşteri geri bildirimlerinden kaynaklanan işlem içi hata ayıklama, 2,0 sürümündeki .NET Framework kaldırılmıştır ve profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4cc41-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cc41-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cc41-112">Requirements</span></span>  
 <span data-ttu-id="4cc41-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cc41-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc41-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4cc41-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4cc41-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4cc41-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cc41-116">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="4cc41-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc41-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cc41-117">See also</span></span>

- [<span data-ttu-id="4cc41-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cc41-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
