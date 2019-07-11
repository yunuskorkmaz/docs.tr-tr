---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21703aa911b5222fff71282e6da26aa5c0e2853
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756847"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="098d4-102">ICorDebugHandleValue::Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="098d4-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="098d4-103">Arabirim işaretçisini açıkça bırakmadan bu Icordebughandlevalue nesne tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="098d4-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="098d4-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="098d4-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="098d4-105">Requirements</span></span>  
 <span data-ttu-id="098d4-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="098d4-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="098d4-107">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="098d4-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="098d4-108">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="098d4-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="098d4-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="098d4-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
