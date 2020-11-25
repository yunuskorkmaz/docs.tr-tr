---
title: ICorDebugFunction2::GetJMCStatus Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 747f165a98dfd1264ea58d61aaa1615c6d71e073
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726304"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="c9d7d-102">ICorDebugFunction2::GetJMCStatus Metodu</span><span class="sxs-lookup"><span data-stu-id="c9d7d-102">ICorDebugFunction2::GetJMCStatus Method</span></span>

<span data-ttu-id="c9d7d-103">Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c9d7d-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d7d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c9d7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9d7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9d7d-105">Parameters</span></span>  

 `pbIsJustMyCode`  
 <span data-ttu-id="c9d7d-106">dışı Boolean değere yönelik bir işaretçi `true` , bu işlev kullanıcı kodu olarak işaretlenmişse; Aksi takdirde değer olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c9d7d-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9d7d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9d7d-107">Remarks</span></span>  

 <span data-ttu-id="c9d7d-108">Bunu temsil eden işlevin `ICorDebugFunction2` ayıklanamayacağını belirlerseniz, `pbIsJustMyCode` her zaman olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c9d7d-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9d7d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9d7d-109">Requirements</span></span>  

 <span data-ttu-id="c9d7d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d7d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d7d-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9d7d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9d7d-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c9d7d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9d7d-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d7d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
