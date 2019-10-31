---
title: ICorDebugStringValue::GetLength Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: a6f2f536d360ffe41caf2a96c8b051f9167343c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138964"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="4dbe2-102">ICorDebugStringValue::GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4dbe2-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="4dbe2-103">Bu ICorDebugStringValue tarafından başvurulan dizedeki karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4dbe2-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dbe2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4dbe2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dbe2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4dbe2-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="4dbe2-106">dışı Bu `ICorDebugStringValue` nesnesi tarafından başvurulan dizenin uzunluğunu belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4dbe2-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dbe2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4dbe2-107">Requirements</span></span>  
 <span data-ttu-id="4dbe2-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dbe2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dbe2-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4dbe2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dbe2-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4dbe2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dbe2-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dbe2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
