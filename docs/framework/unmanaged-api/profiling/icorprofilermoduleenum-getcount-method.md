---
description: ': ICorProfilerModuleEnum:: GetCount metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: efdd812795002c25aaeb7634e7a4f4e4287553e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781395"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="f9891-103">ICorProfilerModuleEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9891-103">ICorProfilerModuleEnum::GetCount Method</span></span>

<span data-ttu-id="f9891-104">Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f9891-104">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9891-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9891-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9891-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9891-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f9891-107">dışı Koleksiyondaki çalışma zamanı modüllerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f9891-107">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9891-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9891-108">Requirements</span></span>  

 <span data-ttu-id="f9891-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9891-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9891-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f9891-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9891-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9891-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9891-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9891-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9891-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9891-113">See also</span></span>

- [<span data-ttu-id="f9891-114">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9891-114">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="f9891-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f9891-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
