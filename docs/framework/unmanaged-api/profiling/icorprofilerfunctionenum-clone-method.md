---
title: ICorProfilerFunctionEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: d6f348eb781efdef89926ec1bc267281bf3a5004
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503113"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="3b2e5-102">ICorProfilerFunctionEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b2e5-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="3b2e5-103">Bu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="3b2e5-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b2e5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3b2e5-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b2e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b2e5-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3b2e5-106">dışı Bu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3b2e5-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="3b2e5-107">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="3b2e5-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="3b2e5-108">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3b2e5-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b2e5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b2e5-109">Requirements</span></span>  
 <span data-ttu-id="3b2e5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b2e5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b2e5-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3b2e5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b2e5-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3b2e5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b2e5-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b2e5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2e5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b2e5-114">See also</span></span>

- [<span data-ttu-id="3b2e5-115">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b2e5-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="3b2e5-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3b2e5-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
