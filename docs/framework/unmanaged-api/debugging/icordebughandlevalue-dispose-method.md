---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıınfo Ghandlivalue::D ispoz yöntemi'
title: ICorDebugHandleValue::Dispose Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: e39ff66137e12ebc939e1e060dd37ea8af9b623a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692062"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="c0a65-103">ICorDebugHandleValue::Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0a65-103">ICorDebugHandleValue::Dispose Method</span></span>

<span data-ttu-id="c0a65-104">Arabirim işaretçisini açıkça serbest bırakmadan, bu ıcorıınfo Ghandlivalue nesnesi tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c0a65-104">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a65-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0a65-105">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="c0a65-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0a65-106">Requirements</span></span>  

 <span data-ttu-id="c0a65-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a65-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a65-108">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0a65-108">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0a65-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c0a65-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0a65-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0a65-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
