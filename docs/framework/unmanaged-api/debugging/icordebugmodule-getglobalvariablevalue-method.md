---
title: ICorDebugModule::GetGlobalVariableValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ad31c3108b1ec8f32640d67a511935599f99515a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="c5aa6-102">ICorDebugModule::GetGlobalVariableValue Metodu</span><span class="sxs-lookup"><span data-stu-id="c5aa6-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="c5aa6-103">Belirtilen genel değişkeni değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c5aa6-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5aa6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5aa6-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5aa6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5aa6-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="c5aa6-106">[in] Bir `mdFieldDef` genel değişkeni açıklayan meta veriler başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="c5aa6-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c5aa6-107">[out] Bir işaretçi adresine Icordebugvalue nesnenin belirtilen genel değişkeni değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5aa6-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5aa6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5aa6-108">Requirements</span></span>  
 <span data-ttu-id="c5aa6-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5aa6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5aa6-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5aa6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5aa6-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5aa6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5aa6-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5aa6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
