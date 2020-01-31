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
ms.openlocfilehash: 8153dbd27e168e3a5bd8e5aeada955a0382aaf75
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868258"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="d5e5c-102">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5e5c-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="d5e5c-103">Bu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) arabiriminin bir kopyasına yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d5e5c-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5e5c-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5e5c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d5e5c-106">dışı Bu `ICorProfilerObjectEnum` arabiriminin kopyasına işaret eden arabirim işaretçisinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d5e5c-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="d5e5c-107">Kopya kendi numaralandırma durumunu bu bilgisayardan ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="d5e5c-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="d5e5c-108">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5e5c-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e5c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5e5c-109">Requirements</span></span>  
 <span data-ttu-id="d5e5c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e5c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e5c-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d5e5c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5e5c-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5e5c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e5c-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e5c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e5c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e5c-114">See also</span></span>

- [<span data-ttu-id="d5e5c-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5e5c-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
