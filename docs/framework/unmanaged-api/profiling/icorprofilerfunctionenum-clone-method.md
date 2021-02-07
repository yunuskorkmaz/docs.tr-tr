---
description: ': ICorProfilerFunctionEnum:: Clone yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6cadadd98f64a27de0cd4e7d264fe797d22c33a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737681"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="4c426-103">ICorProfilerFunctionEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c426-103">ICorProfilerFunctionEnum::Clone Method</span></span>

<span data-ttu-id="4c426-104">Bu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4c426-104">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c426-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c426-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c426-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c426-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="4c426-107">dışı Bu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4c426-107">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="4c426-108">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="4c426-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="4c426-109">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4c426-109">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c426-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c426-110">Requirements</span></span>  

 <span data-ttu-id="4c426-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c426-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c426-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4c426-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c426-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c426-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c426-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c426-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c426-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c426-115">See also</span></span>

- [<span data-ttu-id="4c426-116">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c426-116">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="4c426-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c426-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
