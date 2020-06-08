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
ms.openlocfilehash: 137b1da853535985b2fd383d52f0bcfc48f728ed
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503100"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="c04c2-102">ICorProfilerFunctionEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="c04c2-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="c04c2-103">Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c04c2-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04c2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c04c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c04c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c04c2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c04c2-106">dışı Yüklenen işlevlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="c04c2-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04c2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c04c2-107">Requirements</span></span>  
 <span data-ttu-id="c04c2-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c04c2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04c2-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c04c2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c04c2-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c04c2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c04c2-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04c2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04c2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04c2-112">See also</span></span>

- [<span data-ttu-id="c04c2-113">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c04c2-113">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="c04c2-114">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c04c2-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
