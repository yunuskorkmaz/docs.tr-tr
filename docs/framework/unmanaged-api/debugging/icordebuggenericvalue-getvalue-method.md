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
ms.openlocfilehash: dd1c1ba4a976a10d0c38c5295fff838faf072f51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728114"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="67517-102">ICorDebugGenericValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="67517-102">ICorDebugGenericValue::GetValue Method</span></span>

<span data-ttu-id="67517-103">Bu genel değerini belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="67517-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67517-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="67517-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67517-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67517-105">Parameters</span></span>  

 `pTo`  
 <span data-ttu-id="67517-106">dışı Bu ICorDebugGenericValue nesnesi tarafından temsil edilen değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67517-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="67517-107">Değer bir basit tür veya başvuru türü (yani, bir işaretçi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="67517-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67517-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67517-108">Requirements</span></span>  

 <span data-ttu-id="67517-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67517-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67517-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67517-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67517-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="67517-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67517-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67517-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
