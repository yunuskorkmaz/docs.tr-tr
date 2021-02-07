---
description: ': ICorProfilerModuleEnum:: Clone yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerModuleEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: 0d2a235def6d3b16d661e51979742426ebe1942f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736946"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="78bd7-103">ICorProfilerModuleEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78bd7-103">ICorProfilerModuleEnum::Clone Method</span></span>

<span data-ttu-id="78bd7-104">Bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="78bd7-104">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bd7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78bd7-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78bd7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78bd7-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="78bd7-107">dışı Sırasıyla bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78bd7-107">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="78bd7-108">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="78bd7-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="78bd7-109">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="78bd7-109">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78bd7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78bd7-110">Requirements</span></span>  

 <span data-ttu-id="78bd7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78bd7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bd7-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="78bd7-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78bd7-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="78bd7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78bd7-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78bd7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bd7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78bd7-115">See also</span></span>

- [<span data-ttu-id="78bd7-116">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78bd7-116">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="78bd7-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="78bd7-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
