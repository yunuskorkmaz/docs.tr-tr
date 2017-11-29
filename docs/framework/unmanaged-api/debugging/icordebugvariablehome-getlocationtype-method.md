---
title: "ICorDebugVariableHome::GetLocationType yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a600f26440e29a60d776be8679d7a298d77434f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="27931-102">ICorDebugVariableHome::GetLocationType yöntemi</span><span class="sxs-lookup"><span data-stu-id="27931-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="27931-103">Değişkenin yerel konum türünü alır.</span><span class="sxs-lookup"><span data-stu-id="27931-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27931-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27931-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27931-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27931-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="27931-106">[out] Değişkenin yerel konum türünü gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27931-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="27931-107">Bkz: [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) daha fazla bilgi için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="27931-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27931-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27931-108">Requirements</span></span>  
 <span data-ttu-id="27931-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27931-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27931-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27931-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27931-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27931-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27931-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27931-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27931-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27931-113">See Also</span></span>  
 [<span data-ttu-id="27931-114">ICorDebugVariableHome arabirimi</span><span class="sxs-lookup"><span data-stu-id="27931-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="27931-115">VariableLocationType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="27931-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
