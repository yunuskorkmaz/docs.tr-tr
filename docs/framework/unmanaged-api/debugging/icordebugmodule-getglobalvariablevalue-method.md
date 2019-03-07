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
ms.openlocfilehash: 00e747e43f67533771665313f4d420e4725945cd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485362"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="ad804-102">ICorDebugModule::GetGlobalVariableValue Metodu</span><span class="sxs-lookup"><span data-stu-id="ad804-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="ad804-103">Belirtilen genel değişkeninin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="ad804-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad804-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad804-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad804-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad804-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="ad804-106">[in] Bir `mdFieldDef` başvuran genel değişkeni açıklayan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ad804-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ad804-107">[out] Belirtilen genel değişkeninin değerini temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad804-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad804-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad804-108">Requirements</span></span>  
 <span data-ttu-id="ad804-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad804-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad804-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad804-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad804-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad804-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad804-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad804-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
