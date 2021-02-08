---
description: ': ICorProfilerThreadEnum:: Clone yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 00920484ed6f089f40281ea2590e6d9c27cd3268
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783800"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="f1fbc-103">ICorProfilerThreadEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1fbc-103">ICorProfilerThreadEnum::Clone Method</span></span>

<span data-ttu-id="f1fbc-104">Bu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f1fbc-104">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1fbc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1fbc-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1fbc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1fbc-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="f1fbc-107">dışı Bu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f1fbc-107">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="f1fbc-108">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="f1fbc-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="f1fbc-109">Ancak, kopyanın ilk imleç konumu, Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f1fbc-109">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1fbc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1fbc-110">Requirements</span></span>  

 <span data-ttu-id="f1fbc-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1fbc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1fbc-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f1fbc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1fbc-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1fbc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1fbc-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1fbc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fbc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1fbc-115">See also</span></span>

- [<span data-ttu-id="f1fbc-116">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="f1fbc-116">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="f1fbc-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f1fbc-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
