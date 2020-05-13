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
ms.openlocfilehash: 646b2661148e38f3c918fc18fce5c9cd0b1134a1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213029"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="dfad0-102">ICorDebugGenericValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="dfad0-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="dfad0-103">Bu genel değerini belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="dfad0-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfad0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfad0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfad0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfad0-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="dfad0-106">dışı Bu ICorDebugGenericValue nesnesi tarafından temsil edilen değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfad0-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="dfad0-107">Değer bir basit tür veya başvuru türü (yani, bir işaretçi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="dfad0-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfad0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfad0-108">Requirements</span></span>  
 <span data-ttu-id="dfad0-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfad0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfad0-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dfad0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfad0-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dfad0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfad0-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfad0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
