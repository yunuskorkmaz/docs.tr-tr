---
title: ICorDebugModule::GetGlobalVariableValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd79299dcfdb03b703c2cab214ba448631daa6f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763485"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="29c71-102">ICorDebugModule::GetGlobalVariableValue Metodu</span><span class="sxs-lookup"><span data-stu-id="29c71-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="29c71-103">Belirtilen genel değişkeninin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="29c71-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29c71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29c71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29c71-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="29c71-106">[in] Bir `mdFieldDef` başvuran genel değişkeni açıklayan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="29c71-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="29c71-107">[out] Belirtilen genel değişkeninin değerini temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="29c71-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c71-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29c71-108">Requirements</span></span>  
 <span data-ttu-id="29c71-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c71-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c71-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29c71-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29c71-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29c71-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29c71-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c71-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
