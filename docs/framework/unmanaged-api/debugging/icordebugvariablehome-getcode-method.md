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
ms.openlocfilehash: ee8fa8feebba7258fc84ee7ba00ce2ab1977faa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420410"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="71519-102">ICorDebugVariableHome::GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="71519-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="71519-103">Bu içeren "ICorDebugCode" örneği alır [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="71519-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71519-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71519-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71519-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71519-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="71519-106">[out] Bu içeren "ICorDebugCode" örneği adresini gösteren bir işaretçi [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="71519-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71519-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71519-107">Requirements</span></span>  
 <span data-ttu-id="71519-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71519-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71519-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71519-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71519-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71519-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71519-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71519-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71519-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71519-112">See Also</span></span>  
 [<span data-ttu-id="71519-113">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71519-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 
