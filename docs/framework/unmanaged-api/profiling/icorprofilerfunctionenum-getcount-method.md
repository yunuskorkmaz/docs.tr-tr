---
title: ICorProfilerFunctionEnum::GetCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.GetCount Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ac7e1e4c13578859c02f531dbc3b5e6f01e55cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="47bce-102">ICorProfilerFunctionEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="47bce-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="47bce-103">Uygulama tarafından yüklenen ya da zorla Profil Oluşturucu tarafından yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="47bce-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47bce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47bce-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47bce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47bce-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="47bce-106">[out] Yüklenen işlevleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="47bce-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47bce-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47bce-107">Requirements</span></span>  
 <span data-ttu-id="47bce-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47bce-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47bce-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47bce-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47bce-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47bce-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47bce-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47bce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47bce-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47bce-112">See Also</span></span>  
 [<span data-ttu-id="47bce-113">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47bce-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="47bce-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="47bce-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
