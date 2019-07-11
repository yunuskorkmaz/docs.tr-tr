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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44d3fee49ae74c69b49029208588f4894e250f78
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775204"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="a13cd-102">ICorProfilerModuleEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a13cd-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="a13cd-103">Uygulamaya yüklenen yönetilen modülleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a13cd-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a13cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a13cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a13cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a13cd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a13cd-106">[out] Çalışma zamanı modülleri koleksiyon sayısı.</span><span class="sxs-lookup"><span data-stu-id="a13cd-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a13cd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a13cd-107">Requirements</span></span>  
 <span data-ttu-id="a13cd-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a13cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a13cd-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a13cd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a13cd-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a13cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a13cd-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a13cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13cd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a13cd-112">See also</span></span>

- [<span data-ttu-id="a13cd-113">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a13cd-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="a13cd-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a13cd-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
