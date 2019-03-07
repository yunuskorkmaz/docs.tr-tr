---
title: ICorDebugGenericValue::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53db4dcb13303c9e7bdd77a46b3c9526364bac06
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471231"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="eba33-102">ICorDebugGenericValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="eba33-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="eba33-103">Bu genel değerini belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="eba33-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eba33-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eba33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eba33-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="eba33-106">[out] Bu Icordebuggenericvalue nesnesi tarafından temsil edilen değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eba33-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="eba33-107">Değer, bir basit türü veya başvuru türü (diğer bir deyişle, bir işaretçi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="eba33-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba33-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eba33-108">Requirements</span></span>  
 <span data-ttu-id="eba33-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eba33-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba33-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eba33-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eba33-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eba33-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eba33-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba33-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
