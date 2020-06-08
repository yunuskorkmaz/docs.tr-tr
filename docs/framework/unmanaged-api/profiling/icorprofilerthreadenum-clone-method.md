---
title: ICorProfilerThreadEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: 890bb9bdd3b639d38f4f290eed86ad72b6a53f0f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494455"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="122fe-102">ICorProfilerThreadEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="122fe-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="122fe-103">Bu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="122fe-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122fe-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="122fe-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="122fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="122fe-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="122fe-106">dışı Bu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="122fe-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="122fe-107">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="122fe-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="122fe-108">Ancak, kopyanın ilk imleç konumu, Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="122fe-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122fe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="122fe-109">Requirements</span></span>  
 <span data-ttu-id="122fe-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122fe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122fe-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="122fe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="122fe-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="122fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="122fe-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122fe-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="122fe-114">See also</span></span>

- [<span data-ttu-id="122fe-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="122fe-115">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="122fe-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="122fe-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
