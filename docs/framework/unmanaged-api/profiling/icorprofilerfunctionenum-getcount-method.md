---
description: ': ICorProfilerFunctionEnum:: GetCount metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a3eccfa31676636aff7379b4080bcb85a268df6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737629"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="8065d-103">ICorProfilerFunctionEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="8065d-103">ICorProfilerFunctionEnum::GetCount Method</span></span>

<span data-ttu-id="8065d-104">Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8065d-104">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8065d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8065d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8065d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8065d-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="8065d-107">dışı Yüklenen işlevlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="8065d-107">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8065d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8065d-108">Requirements</span></span>  

 <span data-ttu-id="8065d-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8065d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8065d-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8065d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8065d-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8065d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8065d-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8065d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8065d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8065d-113">See also</span></span>

- [<span data-ttu-id="8065d-114">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8065d-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="8065d-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8065d-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
