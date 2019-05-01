---
title: ICorDebugGenericValue::SetValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae64fcccb49123f34cca2622a972a89bf700904f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995552"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="40339-102">ICorDebugGenericValue::SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40339-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="40339-103">Yeni bir değer belirtilen arabellek kopyalar.</span><span class="sxs-lookup"><span data-stu-id="40339-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40339-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40339-104">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40339-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40339-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="40339-106">[in] Arabellek için işaretçi değeri kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="40339-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40339-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40339-107">Remarks</span></span>  
 <span data-ttu-id="40339-108">Başvuru türleri için başvuru içeriği bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="40339-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40339-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40339-109">Requirements</span></span>  
 <span data-ttu-id="40339-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40339-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40339-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40339-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40339-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40339-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40339-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40339-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
