---
description: ': ICorDebugGenericValue:: GetValue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9c8459ce6a9fb59e934b1ebd355aa091a37b2d7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661070"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="94ef4-103">ICorDebugGenericValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="94ef4-103">ICorDebugGenericValue::GetValue Method</span></span>

<span data-ttu-id="94ef4-104">Bu genel değerini belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="94ef4-104">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ef4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94ef4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94ef4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94ef4-106">Parameters</span></span>  

 `pTo`  
 <span data-ttu-id="94ef4-107">dışı Bu ICorDebugGenericValue nesnesi tarafından temsil edilen değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94ef4-107">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="94ef4-108">Değer bir basit tür veya başvuru türü (yani, bir işaretçi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="94ef4-108">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94ef4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94ef4-109">Requirements</span></span>  

 <span data-ttu-id="94ef4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94ef4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94ef4-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94ef4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94ef4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="94ef4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94ef4-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94ef4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
