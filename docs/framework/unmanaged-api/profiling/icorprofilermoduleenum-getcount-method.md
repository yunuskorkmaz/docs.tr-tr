---
title: ICorProfilerModuleEnum::GetCount Metodu
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
ms.openlocfilehash: 91572887713216f94707e5d21e5767f4cc54e0d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456264"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="a9bad-102">ICorProfilerModuleEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="a9bad-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="a9bad-103">Uygulamaya yüklenen yönetilen modüller sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a9bad-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9bad-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9bad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9bad-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a9bad-106">[out] Çalışma zamanı modülleri koleksiyondaki sayısı.</span><span class="sxs-lookup"><span data-stu-id="a9bad-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bad-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9bad-107">Requirements</span></span>  
 <span data-ttu-id="a9bad-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9bad-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9bad-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9bad-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9bad-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9bad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9bad-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9bad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bad-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9bad-112">See Also</span></span>  
 [<span data-ttu-id="a9bad-113">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9bad-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="a9bad-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9bad-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
