---
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
ms.openlocfilehash: a6b36883ec0914426b4f4c937390c1622faead25
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868297"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="10475-102">ICorProfilerModuleEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10475-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="10475-103">Bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10475-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10475-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10475-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10475-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10475-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="10475-106">dışı Sırasıyla bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="10475-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="10475-107">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="10475-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="10475-108">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="10475-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10475-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10475-109">Requirements</span></span>  
 <span data-ttu-id="10475-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10475-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10475-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="10475-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10475-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="10475-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10475-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10475-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10475-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10475-114">See also</span></span>

- [<span data-ttu-id="10475-115">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10475-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="10475-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="10475-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
