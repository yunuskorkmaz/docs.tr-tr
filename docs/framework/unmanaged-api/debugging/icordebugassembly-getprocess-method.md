---
title: ICorDebugAssembly::GetProcess Metodu
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
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fbb62bb6d2731c5bc2618de0a71f75e0979808c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="f7e34-102">ICorDebugAssembly::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="f7e34-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="f7e34-103">Arabirim işaretçisi bu Icordebugassembly örneğinin çalıştığı işlem alır.</span><span class="sxs-lookup"><span data-stu-id="f7e34-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7e34-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7e34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7e34-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="f7e34-106">[out] İşlemi temsil eden bir Icordebugprocess arabirimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7e34-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e34-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7e34-107">Requirements</span></span>  
 <span data-ttu-id="f7e34-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e34-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e34-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7e34-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7e34-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7e34-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7e34-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e34-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
