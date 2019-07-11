---
title: ICorDebugEval::NewString Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50a18f435063b74b837dbfe9e4f1d986bb735039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753344"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="8204d-102">ICorDebugEval::NewString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8204d-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="8204d-103">Yeni bir dize örneği belirtilen içeriğiyle ayırır.</span><span class="sxs-lookup"><span data-stu-id="8204d-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8204d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8204d-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8204d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8204d-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="8204d-106">[in] İçeriği dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8204d-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8204d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8204d-107">Remarks</span></span>  
 <span data-ttu-id="8204d-108">Dize, her zaman iş parçacığı gerçekleştirmektedir uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8204d-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8204d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8204d-109">Requirements</span></span>  
 <span data-ttu-id="8204d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8204d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8204d-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8204d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8204d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8204d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8204d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8204d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
