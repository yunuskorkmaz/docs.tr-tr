---
description: ': ICorProfilerObjectEnum:: Clone yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 59971f6f6e7edab4b4c4f796ee7bea3c4d8b4e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798959"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="bd8be-103">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd8be-103">ICorProfilerObjectEnum::Clone Method</span></span>

<span data-ttu-id="bd8be-104">Bu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) arabiriminin bir kopyasına yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="bd8be-104">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8be-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd8be-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd8be-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd8be-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="bd8be-107">dışı Arabirim işaretçisinin, bu arabirimin kopyasına işaret eden bir işaretçisi `ICorProfilerObjectEnum` .</span><span class="sxs-lookup"><span data-stu-id="bd8be-107">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="bd8be-108">Kopya kendi numaralandırma durumunu bu bilgisayardan ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="bd8be-108">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="bd8be-109">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bd8be-109">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8be-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd8be-110">Requirements</span></span>  

 <span data-ttu-id="bd8be-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd8be-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd8be-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd8be-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd8be-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bd8be-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd8be-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd8be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8be-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd8be-115">See also</span></span>

- [<span data-ttu-id="bd8be-116">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd8be-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
