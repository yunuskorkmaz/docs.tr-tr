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
ms.openlocfilehash: d246acbf314a83ca3f8113e9a2fb223ac0ebcafe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040930"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="02968-102">ICorProfilerModuleEnum::GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02968-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="02968-103">Uygulamaya yüklenen yönetilen modülleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="02968-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02968-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02968-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02968-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02968-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="02968-106">[out] Çalışma zamanı modülleri koleksiyon sayısı.</span><span class="sxs-lookup"><span data-stu-id="02968-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02968-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02968-107">Requirements</span></span>  
 <span data-ttu-id="02968-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02968-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02968-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02968-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02968-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02968-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02968-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02968-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02968-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02968-112">See also</span></span>

- [<span data-ttu-id="02968-113">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02968-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="02968-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="02968-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
