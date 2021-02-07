---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugFunction2:: GetJMCStatus yöntemi'
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
ms.openlocfilehash: 42c72256df57b96a52737f4a0e5e90d6ba5d4e0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692296"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="aebb3-103">ICorDebugFunction2::GetJMCStatus Metodu</span><span class="sxs-lookup"><span data-stu-id="aebb3-103">ICorDebugFunction2::GetJMCStatus Method</span></span>

<span data-ttu-id="aebb3-104">Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="aebb3-104">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebb3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aebb3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aebb3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aebb3-106">Parameters</span></span>  

 `pbIsJustMyCode`  
 <span data-ttu-id="aebb3-107">dışı Boolean değere yönelik bir işaretçi `true` , bu işlev kullanıcı kodu olarak işaretlenmişse; Aksi takdirde değer olur `false` .</span><span class="sxs-lookup"><span data-stu-id="aebb3-107">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aebb3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aebb3-108">Remarks</span></span>  

 <span data-ttu-id="aebb3-109">Bunu temsil eden işlevin `ICorDebugFunction2` ayıklanamayacağını belirlerseniz, `pbIsJustMyCode` her zaman olur `false` .</span><span class="sxs-lookup"><span data-stu-id="aebb3-109">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aebb3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aebb3-110">Requirements</span></span>  

 <span data-ttu-id="aebb3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aebb3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aebb3-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aebb3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aebb3-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aebb3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aebb3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aebb3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
