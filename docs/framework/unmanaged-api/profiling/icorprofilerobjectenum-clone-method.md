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
ms.openlocfilehash: 7e8a623107e5e03ca36137c253c9bdf0a722d385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456044"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="b121c-102">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b121c-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="b121c-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerobjectenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b121c-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b121c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b121c-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b121c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b121c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b121c-106">[out] Sırayla bu kopyasını işaret arabirim işaretçisi gösteren bir işaretçi `ICorProfilerObjectEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b121c-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="b121c-107">Kopya kendi numaralandırması durumundan ayrı olarak bunu tutar.</span><span class="sxs-lookup"><span data-stu-id="b121c-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="b121c-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu ile aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b121c-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b121c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b121c-109">Requirements</span></span>  
 <span data-ttu-id="b121c-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b121c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b121c-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b121c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b121c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b121c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b121c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b121c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b121c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b121c-114">See Also</span></span>  
 [<span data-ttu-id="b121c-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b121c-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
