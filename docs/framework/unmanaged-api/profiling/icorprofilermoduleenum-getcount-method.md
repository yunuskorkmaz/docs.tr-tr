---
title: ICorProfilerModuleEnum::GetCount Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: 53009a1805056b83047299ebdca8f21d98ad5137
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732989"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="74727-102">ICorProfilerModuleEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74727-102">ICorProfilerModuleEnum::GetCount Method</span></span>

<span data-ttu-id="74727-103">Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="74727-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74727-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="74727-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74727-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74727-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="74727-106">dışı Koleksiyondaki çalışma zamanı modüllerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="74727-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74727-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74727-107">Requirements</span></span>  

 <span data-ttu-id="74727-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74727-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74727-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74727-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74727-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74727-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74727-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74727-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74727-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74727-112">See also</span></span>

- [<span data-ttu-id="74727-113">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74727-113">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="74727-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74727-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
