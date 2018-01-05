---
title: "ICorDebugAssembly::EnumerateModules Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.EnumerateModules
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5bc6aced78d1d7ffc6521bca52bed1b2e232bbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="4f0df-102">ICorDebugAssembly::EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f0df-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="4f0df-103">İçinde yer alan modülleri için bir numaralandırıcı alır `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="4f0df-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f0df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f0df-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f0df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f0df-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="4f0df-106">[out] Numaralayıcı olduğu Icordebugmoduleenum arabirimi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4f0df-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f0df-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f0df-107">Requirements</span></span>  
 <span data-ttu-id="4f0df-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f0df-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f0df-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f0df-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f0df-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f0df-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f0df-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f0df-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
