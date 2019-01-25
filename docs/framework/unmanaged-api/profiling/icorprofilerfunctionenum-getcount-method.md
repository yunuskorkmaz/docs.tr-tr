---
title: ICorProfilerFunctionEnum::GetCount Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7612b46cb0d7879e8e8301ae77d03b931856b85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531713"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="93373-102">ICorProfilerFunctionEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="93373-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="93373-103">Uygulama tarafından yüklenen ya da profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="93373-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93373-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93373-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93373-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93373-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="93373-106">[out] Yüklenen işlevlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="93373-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93373-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93373-107">Requirements</span></span>  
 <span data-ttu-id="93373-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93373-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93373-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93373-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93373-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93373-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93373-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93373-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93373-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93373-112">See also</span></span>
- [<span data-ttu-id="93373-113">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93373-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="93373-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93373-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
