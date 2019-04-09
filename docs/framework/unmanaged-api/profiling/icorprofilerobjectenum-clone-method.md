---
title: ICorProfilerObjectEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14e8086532eff5dba6883575cc2daf447a32343a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182370"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="2b7d6-102">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b7d6-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="2b7d6-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerobjectenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2b7d6-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b7d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b7d6-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b7d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b7d6-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2b7d6-106">[out] Sırayla bu kopyasını işaret eden bir arabirim işaretçisi için bir işaretçi `ICorProfilerObjectEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2b7d6-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="2b7d6-107">Bu hesaptan ayrı olarak kendi sıralaması durumu kopyasını tutar.</span><span class="sxs-lookup"><span data-stu-id="2b7d6-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="2b7d6-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu ile aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2b7d6-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b7d6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b7d6-109">Requirements</span></span>  
 <span data-ttu-id="2b7d6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b7d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b7d6-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b7d6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b7d6-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b7d6-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2b7d6-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2b7d6-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b7d6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b7d6-114">See also</span></span>

- [<span data-ttu-id="2b7d6-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b7d6-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
