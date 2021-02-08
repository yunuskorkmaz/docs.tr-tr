---
description: ': ICorProfilerInfo:: Getınprocinspectionınterface yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5b7ce053f0a64afd5d702a4eb59c1712f4b26e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781473"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="0d245-103">ICorProfilerInfo::GetInprocInspectionInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d245-103">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>

<span data-ttu-id="0d245-104">Bir "ICorDebugProcess" arabirimi için sorgulanabilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="0d245-104">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="0d245-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0d245-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d245-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d245-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d245-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d245-107">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="0d245-108">bir arabirim için sorgulanabilen [Çıkış](/cpp/atl/iunknown) nesnesi `ICorDebugProcess` .</span><span class="sxs-lookup"><span data-stu-id="0d245-108">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d245-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d245-109">Remarks</span></span>  

 <span data-ttu-id="0d245-110">Ortak dil çalışma zamanı (CLR) hata ayıklama API 'SI .NET Framework 1,0 sürümünde sınırlı sayıda işlem hata ayıklaması destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="0d245-110">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="0d245-111">İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="0d245-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="0d245-112">Müşteri geri bildirimlerinden kaynaklanan işlem içi hata ayıklama, 2,0 sürümündeki .NET Framework kaldırılmıştır ve profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d245-112">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d245-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d245-113">Requirements</span></span>  

 <span data-ttu-id="0d245-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d245-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d245-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d245-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d245-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0d245-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d245-117">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="0d245-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d245-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d245-118">See also</span></span>

- [<span data-ttu-id="0d245-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d245-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
