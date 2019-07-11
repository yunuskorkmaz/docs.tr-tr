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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b13fe65f892a222abb126aa9237b802507738b7f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771614"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="f6a4f-102">ICorDebugStringValue::GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6a4f-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="f6a4f-103">Bu Icordebugstringvalue tarafından başvurulan dizedeki karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f6a4f-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6a4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6a4f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6a4f-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="f6a4f-106">[out] Bu tarafından başvurulan dize uzunluğunu belirten bir değer için bir işaretçi `ICorDebugStringValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="f6a4f-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6a4f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6a4f-107">Requirements</span></span>  
 <span data-ttu-id="f6a4f-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6a4f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6a4f-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6a4f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6a4f-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6a4f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6a4f-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6a4f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
