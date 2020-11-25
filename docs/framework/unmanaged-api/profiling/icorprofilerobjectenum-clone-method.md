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
ms.openlocfilehash: df1d5881bccdb357b16c7f02cd090388e0f66273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722810"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="eba19-102">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eba19-102">ICorProfilerObjectEnum::Clone Method</span></span>

<span data-ttu-id="eba19-103">Bu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) arabiriminin bir kopyasına yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="eba19-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba19-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eba19-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eba19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eba19-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="eba19-106">dışı Arabirim işaretçisinin, bu arabirimin kopyasına işaret eden bir işaretçisi `ICorProfilerObjectEnum` .</span><span class="sxs-lookup"><span data-stu-id="eba19-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="eba19-107">Kopya kendi numaralandırma durumunu bu bilgisayardan ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="eba19-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="eba19-108">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="eba19-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba19-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eba19-109">Requirements</span></span>  

 <span data-ttu-id="eba19-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eba19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba19-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eba19-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eba19-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eba19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eba19-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba19-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eba19-114">See also</span></span>

- [<span data-ttu-id="eba19-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eba19-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
