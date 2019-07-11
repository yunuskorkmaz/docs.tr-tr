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
ms.openlocfilehash: 72df5a5c2d0ef4bc462eeaa43f2d55a3d2a56fe4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775030"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="b8a58-102">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8a58-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="b8a58-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerobjectenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b8a58-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8a58-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8a58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8a58-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b8a58-106">[out] Sırayla bu kopyasını işaret eden bir arabirim işaretçisi için bir işaretçi `ICorProfilerObjectEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b8a58-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="b8a58-107">Bu hesaptan ayrı olarak kendi sıralaması durumu kopyasını tutar.</span><span class="sxs-lookup"><span data-stu-id="b8a58-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="b8a58-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu ile aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b8a58-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a58-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8a58-109">Requirements</span></span>  
 <span data-ttu-id="b8a58-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8a58-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8a58-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8a58-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8a58-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8a58-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8a58-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a58-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a58-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8a58-114">See also</span></span>

- [<span data-ttu-id="b8a58-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8a58-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
