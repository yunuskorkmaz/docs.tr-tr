---
title: ICorDebugVariableHome::GetCode yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c9b334535f8f6652f30a4b5c9de64bde435c3bd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496228"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="7aac4-102">ICorDebugVariableHome::GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="7aac4-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="7aac4-103">Bu içeren "ICorDebugCode" örneğini alır [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="7aac4-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aac4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7aac4-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aac4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7aac4-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7aac4-106">[out] Bu içeren "ICorDebugCode" örneğini adresini bir işaretçiye [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="7aac4-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aac4-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7aac4-107">Requirements</span></span>  
 <span data-ttu-id="7aac4-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aac4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aac4-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7aac4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aac4-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aac4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aac4-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aac4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aac4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aac4-112">See also</span></span>
- [<span data-ttu-id="7aac4-113">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7aac4-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

